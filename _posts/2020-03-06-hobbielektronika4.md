---
title: Hobbielektronika - Mikrokontroller IO pin alapozó (Part 1)
layout: post
author: montyx
categories: electronics
tags: hobbielekronika elektronika táp mcu esp8266 arduino pinout atmega328
---
Az előző posztom publikálása után nagyon sok segítséget kaptam a Hobbielektronika csoport tagjaitól. Örökké hálás leszek érte, és a jövőben is szívesen látok hasonló nagyon jó építő jellegű kritikát. Így a mai témám esetén is.
Ezek pedig egy panel, illetve a rajta található MCU lábai. Hogy lehet megtudni, hogy melyik IO pin mit tud? Ami fontos, hogy ne ijedjünk meg tőle. Hirtelen soknak fog tűnni, de próbállak titeket végigvezetni ezen a dzsungelen.
Igazság szerint az MCUk használatának a lényege, hogy az IO Pinek (Input Output Pinek - ki és bemeneti lábak) állapotát vagy kiolvassuk, vagy megváltoztassuk. Persze vannak ennél bonyolultabb esetek is, de majd azokról kicsit később. Minden MCU adatlapjának nagyon fontos része a láb kiosztás. Angolul PIN Layout. Mutatok is egy példát, egy Arduino UNO-t. (A képre jobb klikk, majd megnyitás új lapon/ablakban, és teljes méretében látni fogod)

| ![Arduino UNO lábkiosztása](/docs/assets/arduino-uno-pinout.png) | 
|:--:| 
| *Arduino UNO lábkiosztása* |

Azért az UNOt választottam, mert jól ismert board, illetve ezt is ajánlottam beszerzésre. No tehát, nem kell megijedni a rengeteg információtól a képen. Van itt minden, mi szem-szájnak ingere, és ez még nem is a bonyolultabb panelek/MCUk közül való. Szerintem ATMega328/Arduino boardok pont az elégséges tudásuk, és nagyon jó támogatottságuk miatt lettek közkedveltek. Se nem volt sok, se nem kevés. Lehet kísérletezni és projekteket csinálni a használatukkal, de még nem egy túl bonyolult darab. Kezdőknek tényleg ideális. Okosan egyszerű.
Nem fogok most egyesével végigmenni a lábakon, meg a feltüntetett képességeken. Ezekről későbbi posztok során fogok írni, mindig egy-két képességre koncentrálva. Amit itt meg akarok mutatni az az, hogy hogyan kell olvasni a képet. Vannak azonos, és különböző tudású pinek. Sőt a legtöbb pin több célra is használható, persze egyszerre csak egyre. Ebben a posztban a board két oldalán található csatlakozási pontokra fogok csak koncentrálni. Kezdésnek ez is elég lesz.

Minden pinnek, minden MCU, és panel esetében van egy azonosítója, ez legtöbbször egy szám, vagy egy két karakteres jelzés. Ezen kívül vannak olyanok, ami mellett egy rövid szöveg van csak. Ezek nem programozható pinek, hanem például áram ki és bemenetek. Ezek az UNO esetében a képen bal felül található pinek egy része. Rájuk gondolok:

| ![Power pinek](/docs/assets/arduino-uno-power-pins.png) | 
|:--:| 
| *Power pinek* |

Ők a power pinek, vagy nevezzük őket most áram ellátási pineknek (ha valaki tud jobb fordítást, ne kíméljen). Fentről lefelé:
**3V3**: Ezen a pinen keresztül 3.3V feszültséget tud leadni a panel szenzorok és egyéb perifériák megtáplálására.
5V: Ugyanez, csak 5V feszültséggel. Elvileg használható mindkettő áramellátásra is, de a gyártó kimondottan nem ajánlja, ugyanis nem szabályzott bemenetek. Így magasabb feszültség esetén könnyű tönkretenni a panelt ezen lábak ilyen célú használatával.
**GND**: földelési pin. Fontos, hogy közös földre legyen kötve minden vezérelt periféria a panellal. Ezen pinek segítségével lehet ezt megoldani.
**VIN**: Ez egy speciális pin. Szabályozott bemenet. 7-12V betápot ajánl az Arduino oldal erre a bemenetre. Arra lehet használni, hogy külső áramforrásról tápláljuk meg vele a panelt. Általában akkor használjuk, ha már túl vagyunk a panel-MCU programozáson, és csak használni akarjuk a végeredményt. Így USBn keresztül már nincs a számítógépre kötve, illetve nem akarjuk a DC csatlakozót se használni (a kép bal tetején).

Ahogy említettem vannak a szám-azonosítókkal ellátott pinek. Ezzel el is jön az a rész, ami elsőre minden kezdőt a pokol tornácára kerget. Tiszta katyvasz az egész:

| ![Pin elnevezések](/docs/assets/arduino-uno-io-pins.png) | 
|:--:| 
| *Pin elnevezések* |

Van itt minden kérem szépen. Bekereteztem pár jelölést. A piros keretesek a boardon vannak, míg a kékkel jelöltek melléjük lettek írva valamiért. Van bal felül egy egyes szám, jobb alul a kettes, jobb felül egy-egy 27es, meg 28as, majd bal alul is ugyanaz. Tiszta őrültekháza!
Hogy még jobban összezavarjalak, a panelre festett feliratok pedig köszönő viszonyban nincsenek ezzel az egésszel. De tudom még tetézni azzal is, hogy a mellé írt számok közül hiányoznak is egyesek. Ezek a 7-10ig, illetve a 20as, és 22es. Mi ez? Valami őrült tudós agyszüleménye?
Mutatok egy másik képet, hátha segít a megértésben:

| ![ATMega328 pin kiosztása](/docs/assets/atmega328-pinout.png) | 
|:--:| 
| *ATMega328 pin kiosztása* |

Lehet páran már már fel is sikoltottatok, és táncra perdültetek örömötökben, mert látjátok az összefüggést. A panel mellé írt számok egyeznek az ATMega328 lábkiosztásával. Egyszerűen oda vannak kikötve az MCU egyes lábai. Amint látjuk a 20-22es lábak power pinek, illetve egy AREF. Ez most nem olyan fontos, külső feszültség referencia pin. A másik négy hiányzó pedig a másik oldalon van. A 7-10ig. Ezek közül a 7-8 power és ground, azaz áram és föld pinek. A 9-10 pedig két kristály oszcillátor kapcsolati pin. Ebbe most nem mennék bele mélyebben. A lényeg, hogy a számok az ATMega328 fizikai pinjeit jelölik. A boardon található számok pedig egyértelműen saját sorszámozás, illetve az analóg pinek esetén kiemelve egy A betűvel, hogy ők az analógok.

Úgy gondolom kezdésnek elég is lesz ennyi. Legközelebb innen folytatom, mert a lábkiosztás, vagy PIN layout nagyon fontos lesz a programozásuk során. Hasonló képeket lehet találni a legtöbb MCUról és fejlesztői panelről is. Én maradni fogok az Arduino UNO-nál, ha ezt megérted, akkor a többi olvasása se fog problémát okozni. De ehhez még kelleni fog pár poszt.

#### Hasznos linkek
[NodeMCU/ESP8266 pin kiosztásról egy cikk](https://randomnerdtutorials.com/esp8266-pinout-reference-gpios/)  
[ESP32 pin kiosztásról egy cikk](https://microcontrollerslab.com/esp32-pinout-use-gpio-pins/)  
[ATTiny85ről egy nagyon részletes bemutató cikk](https://www.theengineeringprojects.com/2018/09/introduction-to-attiny85.html)  
[STM32F103C8T6 Blue pillről egy még részletesebb dokumentáció](https://os.mbed.com/users/hudakz/code/STM32F103C8T6_Hello/wiki/Homepage)