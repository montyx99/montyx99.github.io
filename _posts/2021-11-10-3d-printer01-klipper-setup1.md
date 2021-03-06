---
title: 3D printing - Klipper gyorstalpaló (1. rész - elmélet)
layout: post
author: montyx
categories: 3d-printing
tags: klipper 3d-printing 3d-printer marlin install raspbian raspberryos
---
A Klipper nyomtató vezérlésben 2 fontos egység vesz részt: a Raspberry PI és a nyomtató alaplapja.A nyomtató alaplapján van egy mikrokontroller, ami a nyomtató összes szenzorát, motorját, motor driverét, fűtési és hűtési egységeit vezérli. A Marlin firmware úgy működik, hogy mindent megoldjon maga az MCU (mikrokontroller). Ugyanis egy slicer által előállított gcode olyanokat tartalmaz, amiket még ki kell számolni geometriával és elemi koordinátákra le kell bontani.

Na most az SWX1 agya egy 8-bites MCU, az ATMEGA2560.

| ![ATmega2560 chip](/docs/assets/atmega2560.png) | 
|:--:| 
| *ATmega2560 chip* |

Ez kb. annyit tud, mint egy alap Arduino Uno. Semmivel sem többet, legalábbis számítási kapacitásban. Cserébe marha sok lába van.

| ![ATmega328 chip](/docs/assets/atmega328p.png) | 
|:--:| 
| *ATmega328 chip* |

Azért látszik a lábmennyiségben a különbség szerintem.

Tehát ezek 8bitesek. Lassan tudják feldolgozni az aritmetikai műveleteket, ezért bonyolult kialakítású (delta, coreXY stb), vagy gyors nyomtatók vezérlésére önmagában alkalmatlanok. A bonyolult nyomtatóknál az a gond, hogy ami a gcode-nak x y és z koordináta, az a nyomtatónak XY, XZ, YZ kettős koordináta lesz, mert egyszerre két motort kell egyenes mozgáshoz mozgatnia. (Persze ez nagyon le van egyszerűsítve, mert hosszú téma lenne) így még ezeket a számításokat is el kell végeznie egy 8bites MCUnak. Kb. ezért voltak nagyon kicsik és lassúak a régi delták.

Na most egy alaplap, az nem más, mint valamilyen értelmezhető formában ezeket a lábakat kivezetni a különböző funkciókhoz. Pl. hasraütve a 13-as pin lesz a bltouch érzékelő vezetéke. Ez azért szükséges, mert kellenek az MCU mellé kísérő dolgok, mint kvarcok, meg ellenállások, diódák, stb. Illetve azért, hogy vérpistike rá tudjon dugni egy csatlakozót, ne kelljen forrasztgatnia. A kis lábakra nem lenne túl egyszerű ugye dugdosni egy motor driver összes lábát. 😃

No és akkor itt jön a Marlin, ami nem csinál mást, mint megmondja a nyomtatónak, hogy most az egyik motor balra, vagy jobbra tekerjen, az azt jelenti, hogy mittomén a 47-49 pinek ilyen, meg olyen állapotba kerüljenek. Tehát emberi olvasható nyelvről lefordítja az MCU nyelvére a kódot, ami értelmezni tudja a kapott gcode-ot és vezérelni tudja a benne lévő egységeket. Ami a gond, hogy ugye mivel MCU-n fut, így tud elég nagy szívás lenni a fordítása és flashelése. Ami azért is veszélyes művelet, mert rossz kód esetén akár ki is égethet alkatrészeket a boardon, vagy magán az MCU-n. Ezt persze a Marlin írói igyekeztek levédeni, de vannak tehetséges próbálkozók mindig.

A Marlin igazi erőssége a 32bites MCUkon jön ki. Ezekre példa az STM32 gyártó 32bites csipjei, melyeket előszeretettel használnak 32bites vezérlőkön. Azért ezeken pörög a Marlin, mert sokkal gyorsabban végzik el a szükséges aritmetikai és matematikai műveleteket, mint a 8bites társaik.

No akkor jöjjön a hosszas bevezető után a Klipper. Van ugye egy RPInk. Legyen mondjuk egy RPI4. Ez bármelyik alaplapban található MCUhoz képest egy atomerőmű. De tényleg. Egy régebbi laptopnak simán megfelel a számítási kapacitása, teljes értékű GUIval rendelkező linux OS fut rajta röccenés nélkül. Amíg az MCU kb. sorfolytonos kódokat tud majdcsak értelmezni, addig a 4 magos chippel szerelt RPI ugye konkurrens szálkezeléssel megtámogatott kódbázisra épült. Tehát gördeszka vs. Porsche Carrera GT.

Ami történik a Klipper telepítésekor az az, hogy egy nagy halom Python kód kerül az RPI-re. A Klipper "szerveroldala" viccesen mondva. Tehát maga a Klipper gcode értelmező motorja, az Octoprint, vagy Moonraker server backend és a két UI, a fluidd, vagy a Mainsail egyike. Az Octoprint és a Moonraker abban különbözik, hogy az előbbi egy teljes 3D printer manager szerveroldali app. Millió plugin, de magától csak valamely RepRap alapú firmwares (pl marlin) géppel tud összepofázni. Tehát önmagában az Octo nem számol semmit sem!!!!!!! Az octo arra jó pl, hogy böngészőből tudod etetni a nyomtatódat gcode fájllal. Nem kell azt SD kártyára másolnod és megdugni vele a nyomtatót. Meg persze ezen kívül sok mindent. De a lényeg, hogy továbbra is valamely komplex firmware fut a nyomtatódon. Viszont a Klipper eredetileg egy Octoprint pluginként indult, hogy a számítást a gördeszkáról a Porschera tegye át.

Itt jött a képbe a Moonraker, ugyanis sokan, köztük én is úgy gondolták, hogy az Octo tök feleslegesen van agyon csillivillizve mindenféle kiegészítővel. Felét nem használja az ember. Pont annyi érdekli, amit a klipper magában is tud. Erre pár okos megírta azt a részt az Octoból, ami kell ahhoz, hogy a klipper magában is működjön. Kis kód és script, illetve macro értelemező, illetve ő nyújtja a webes UI számára szükséges webes API végpontokat is. Ezen kívül tudja az MQTT-t, a Home Assistant integrációt, különböző távoli eszközök managementkét, mint pl. TP-Link és Tasmota smart plugokat stb. De semmi többet. Egy marha minimalista cucc. Csak a szükséges minimumot tudja. A mainsail, meg a fluidd pedig két könnyen használható böngészős felület a klipperhez. Ennyi, nem több.

No és akkor hol a fenében van a nyomtató alaplap firmware a Klipper esetében? Hát ott, hogy a Klipper nem csak "szerveroldali", hanem nyomtató oldali is. A Klipper telepítése során meg kell mondani, hogy az RPI hogy éri el az alaplapot (Pl. USB), milyen csip van a boardon (atmega, stm32 stb.) és az alapján fordít egy halál buta firmware-t. Ez leegyszerűsítve csak annyit tud kb., hogy az MCU melyik PINjére, lábára mikor kell feszültséget adni, vagy onnan kiolvasni a jelenlegi értéket. Nem tudja, hogy vannak rádugva szenzorok, driverek, motorok stb. Csak annyi, hogy most kérlek az analóg 37es PIN kerüljön HIGH állapotban és utána a digitális 23as PIN értékét olvasd be.

A többit a Moonraker és főleg a Klipper csinálja. A különböző makrókat értelmezi a Moonraker, a különböző gcode-okat pedig a klipper. A kettőt a Klipper összegyúrja és a Moonraker kitolja az utasításokat USB-n az alaplapra, majd a kapott választ kiolvassa és együtt értelmezik. Mindezt az RPI csip sebességével.

Ezért általában felesleges 8bitesnél jobb alaplap, ha van Klipper, mert nem terheljük az MCU-t kb . semmivel. Egyedül akkor jön jól egy 32bites, ha már kevés a láb. A 32bites csipeken akár 2-4x annyi láb van, mint egy atmega2560on. Ezért lehet pl. 8 db motor driver rajtuk.

Nagyjából ezek lennének az elméleti alapok. A következő részben írok egy rövid és tömör telepítést, ahogy én a legegyszerűbbnek tartom jelenleg a Klipper multi-instance telepítését és karbantartását. A kommentekben, vagy Facebookon a magyar 3D printer csoportokban megtaláltok a kérdéseitekkel.

A nyomi legyen veletek!