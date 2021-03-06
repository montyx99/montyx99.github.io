---
title: 3D printing - Klipper gyorstalpaló (2. rész - OS telepítés és előkészületek)
layout: post
author: montyx
categories: 3d-printing
tags: klipper 3d-printing 3d-printer marlin install raspbian raspberryos
---
Az első részben nagyjából igyekeztem összefoglalni, hogy miért jó a Klipper firmware és app. Most perid megpróbálom röviden és tömören leírni, hogy szerintem hogyan érdemes telepíteni, akár több példányban is. Az RPI4 4GB-ra több példányban telepítve egyszerre több nyomtatót is lehet az RPI segítségével vezérelni. Ez a második rész magáról a Raspbian telepítéséről fog szólni, így aki azzal képben van ezt a cikket nyugodtan ugorja át.

#### Szükséges eszközök
- Raspberry Pi 3+, 4B, 400 valamelyike.
- min. 16GB SD kártya
- 3D nyomtató(k)
- USB kábel(ek)
- Ethernet kábel (nem kötelező, de ajánlott)
- Sok-sok türelem

#### Szükséges alkalmazások
- Raspbian (Raspberry OS)
- Git
- wget
- Vim, vagy más editor
- Windows PC esetén Putty
- Böngésző (Chrome, Firefox, Edge, Safari stb.)

### Előkészületek

Csapjunk hát bele a lecsóba.

> Először is szeretném kiemelni, hogy én Linux-os gépeket használok itthon, ezért Windows alól a szükséges dolgokat csak linkelni fogom, nem térek ki pl. a Putty használatára. Másodszor pedig nekem külső USB SSD-n fut a Raspbian, ami azért nem triviálisan megoldható és elég sokat szívtam vele mire működött végre.
>
> Szintén fontosnak tartom megemlíteni, hogy eredeti tervek alapján a meglévő ArchARM OS-re szerettem volna a már meglévő Docker konténeres környezetemre a Klippert felrakni, de annyira nem kiforrott még, hogy két hónap méteres kékeres után feladtam. Aztán maradva ArchARMon próbáltam szintén az alábbiakban leírtakat megvalósítani, de ott is olyan falakba ütköztem, amihez már nem volt energiám. Így maradt sajnos a Raspbian. de így legalább rendesen működik a dolog.

Ezeket figyelembe véve az alábbi folyamatot tartom a legegyszerűbbnek. Ugye össze kell rakni az RPI-t, bele kell dugni a hálókábelt és a táp-, illetve a nyomtatóba dugott USB kábelt a közelében elhelyezni. Következő lépés a Raspberry OS Lite verzió letöltése. Aki szeretne magának kísérletezni leszedheti persze valamelyik grafikus felülettel megáldott verzióját is, de ehhez a projekthez halál felesleges.  
[Rapsberry OS](https://www.raspberrypi.com/software/operating-systems/)  
Lehet használni Windows alól a Raspberry Pi Imager-t is, nálam ez nem jött szóba, mert Arch linuxon feleslegesnek tartottam.  
[Raspberry Pi Imager](https://www.raspberrypi.com/software/)  
Ezek után az SD kártyát be kell dugni a PCbe, amire letöltöttük az Image fájlt és/vagy az Imager-t és ki kell rá írni az image-t. Linux alól a parancs:
```bash
sudo dd if=RaspberryPiCustom.img of=/dev/mmcblk0 bs=4m
```
Persze ehhez meg kell keresni a megfelelő .img fájlt és az SD kártya elérhetőségét is. Az előbbire a böngészőből megadott letöltési mappát kell megkeresni, míg az utóbbi esetében a legegyszerűbb módszer az alábbi parancs kiadása:
```bash
lsblk
```
Erre valami hasonlót kell kapni:

| ![lsblk eredménye](/docs/assets/lsblk.png) | 
|:--:| 
| *lsblk parancs eredménye* |

Nekem az utolsó `mmcblk0` az SD kártyám. Nem szabad összekeverni a rajta lévő partíciókkal, tehát a p1 és p2 végűekkel, mert hibát fog dobni a `dd` parancs. Ennyi infóval már lehet is dobni fel a cuccot az SDre a feljebb leírt `dd` paranccsal. Windows esetén használjátok a Pi Imager-t. Ott a Lite verziót és az SD kártyát kiválasztva fel lehet dobni az image-t a kártyára.

> **FONTOS!!!** Mindent le fog törölni a kártyáról, így jól nézd meg előtte, hogy mi van rajta!

OK, akkor kész az SD kártyán az OS. Hát persze, hogy nem. Itt jön az első buktató. Ha most beledugjátok az RPI-be és elindítjátok azt, akkor nézünk, mint Rozi a moziban, hogy érjük el az RPI-t hálózaton keresztül. Leginkább sehogy. Ugyanis az SSH a RPI OS Lite verziójában nincs alapértelmezetten elindítva. Érted?! Jó, mert én sem.

Tehát a teendő, hogy mielőtt a PCből kiveszed a kártyát, azelőtt a `/boot` partíción létre kell hozni egy `ssh` (**Windows userek esetén fontos, hogy kiterjesztés nélkül!**) nevű fájlt. Ezzel triggereljük az RPI OS-t, hogy legyen már kedves hálózaton elérhetővé tennie magát a drága. Ezzel a PC-ből ki lehet végre venni a nyomorult SD kártyát és be lehet végre dugni a helyére, az RPI-be. Bekötjük a hálókábelt, ha még nem tettük meg, illetve bedugjuk a tápot.

### RPI konfigurálása
Első dolog, hogy hogy kell megtalálni a hálózaton az RPI-t. Legegyszerűbb ezt úgy megtenni, hogy megnézzük a routeren, hogy milyen új IP jelent meg. Másik megoldás, hogy egy IP scanner-t használva megnézzük, hogy mi jelent meg a hálózaton. Én erre Arch alatt az Angry IP Scanner-t használom, de rengeteg más hasonló app is van. Windows alatt szintén használható az Angry. Android telóról a bájos nevű Fing alkalmazás tökéletesen megfelel a célnak.

Amint megvan az új IP, Windows esetén Putty-val, Linux esetén a következő paranccsal tudunk csatlakozni az RPI-re:
```bash
ssh 192.168.1.15 -l pi
```
Természetesen az IP-t cseréld ki a sajátodra. Ezt csak példának írtam. A pi user alap jelszava: `raspberry`. Ezt kell beírni a megjelenő prompt esetén. Windows és Putty esetén emlékeim szerint előbb be kell írni a usernevet is, ami értelemszerűen a pi.

#### Nagyon alap biztonság
Fontos pár nagyon alapvető dolgot megtenni az Raspbianon. Ezek nélkül egy kétpálcás hülyegyerek is fel tudja törni az RPI-t.

Állítsd át a pi user jelszavát az alábbi paranccsal:
```bash
passwd
```
Frissítsd le a Raspbian repókat:
```bash
sudo apt update
```
Frissítsd le az OS-t és az alapból telepített alkalmazásokat:
```bash
sudo apt dist-upgrade
```
Hozz létre magadnak egy új usert. Nem jó a pi usert használni.
```bash
sudo useradd -m ujuser
```
Állíts be egy jelszót az új usernek (lehetőleg erőset):
```bash
sudo passwd ujuser
```
Utána add hozzá a megfelelő csoportokhoz:
```bash
sudo usermod -aG dialout ujuser
sudo usermod -aG tty ujuser
```
Majd vedd fel a sudo userek közé:
```bash
sudo usermod -aG sudo ujuser
```
Indítsd újra az RPI-t:
```bash
sudo reboot
```
Pingetéssel tudod nézni, hogy mikor érhető el az RPI:
```bash
ping 192.168.1.15
```
Amikor megvan, akkor SSH az új userrel:
```bash
ssh 192.168.1.15 -l ujuser
```
Végül távolítsd el a pi-t a sudo groupból:
```bash
sudo gpasswd -d pi sudo
```
Telepítsd fel a szükséges alkalmazásokat:
```bash
sudo apt install git wget
```
### Végszó (egyelőre...)
Ezzel a lépéssel meg is vagyunk az előkészületekkel. Természetesen sok mindent lehetne még tenni az RPI biztonságáért. Pl. certificate alapú bejelentkezést, hogy ne kelljen jelszót begépelni SSH csatlakozás esetén, illetve hogy csak megbízható gépekről tudj SSHzni stb. Ezeket már rádbízom. Rengeteg akár magyar nyelvű tutorial van ezekről, így csak azt tudom mondani, hogy hajrá!

Innentől a Klipper telepítéssel folytatom, majd legközelebb.