---
title: Hobbielektronika - Mikrokontrollerekről kezdőknek (Intro)
layout: post
author: montyx
---
Az előbbi két posztom olvasószámát látva úgy döntöttem, hogy folytatom a blogomon a hobbielektronika világában folytatott csetlésem-botlásom kapcsán felgyülemlett tudásom megosztását, hogy másokat is bátorítsak ugyanerre. Ha csak egy valakinek meghozom a kedvét a ténfergésre, akkor már megérte! :)

No akkor essen szó miről is lesz itten szó. Programozással foglalkozom lassan 15 éve. Ezért az elektronika világát is erről az oldalról közelítettem meg. Ami másnak homály, az nekem előny, ami másnak könnyű, az nekem meg pont nehéz emiatt. Én egyből mikrokontrollerek kódolásával kezdtem. Ha LED villogott, már örültem.
Sokkal jobban értem ezeknek a vackoknak a belső világát, mint hogy hogy kell kiszámolni a szükséges kondik, ellenállások stb. méretét. De persze ezek is nagyon fontos dolgok, és már sokkal többet tudok, mint egy évvel ezelőtt.
Előre kiemelném. Ez nem egy szakmai cikk. Itt közérthető nyelven próbálok meg beszélni. Igyekezni fogok a terminus technikusok mellőzését, arra nálam sokkal hozzáértőbb emberek videóit, blogbejegyzéseit érdemes megtekinteni, elolvasni. Ez csak egy amolyan ízelítő.

Szóval mi is az az izé...
Mi is az a mikrokontroller (MicroController Unit, azaz MCU)?
Az MCU nem más, mint egy mini számítógép. Nagyon mini. Vannak be, és kimenetei, lehet rá eszközöket kötni, tud műveleteket végezni, stb. Minden MCU más-más tudással rendelkezik. Van amelyikben marha gyors a központi feldolgozóegység, van aminek rengeteg csatlakozási pontja van, van amelyiknek pont fordítva, nagyon kevés, hogy hihetetlenül kicsi helyen el tudjon férni.
De mindegyiknek van pár közös pontja. Ha felnyitnánk egy Arduino lelkét, azaz az ATMega328 MCUt, akkor valami ilyesmit látnánk benne:
integrated circuit - What is a "DIE" package? - Electrical ...

| ![IC belseje](/docs/assets/Yamaha_YMF262_audio_IC_decapsulated.jpg) | 
|:--:| 
| *IC belseje* |

A képen látható, hogy valaki már szép piros (narancs? barack? Az asszony tuti tudná, hogy lazac :D) vonalkákkal fel is osztotta a chip területét. Ezek közül párat kiemelnék, ami fontos:
**CPU**: ez a központi feldolgozási egység. Az agy. Van sokféle, 8-bit, 32-bit, egymagos, többmagos, stb.
**ISP Flash Memory**: Ez az a memória terület, ahol a bootloader, és maga a kód, amit megírsz fog tárolódni. Ez nem felejtő memória, azaz áramtalanítás után is megmarad a tartalma.
**SRAM**: ez a hagyományos ideiglenes memória (áramtalanításkor ürül) terület. Ezt használja a kód futása során a CPU, hogy ideiglenes adatokat tároljon el benne, amire a futáshoz szüksége van.
**EEPROM**: Nem mindig van ilyen, de gyakori, vagy emulált. Azaz más nem felejtő memória területből a bootloader oldja meg, hogy legyen egy ilyen nevű rész létrehozva.  Nagyon megbízható, hosszan tárolja nagy biztonsággal az adatokat, nagyon gyors írási sebességgel rendelkezik, és akár 1.000.000 újraírási ciklust is elvisel. Cserébe általában nagyon kis tárolási méretű. Ezért okosan kell használni, hogy ne teljen be. Míg a következő SPI Flashből megabájtnyi méretek is gyakoriak, addig EEPROMból az ATMega328 esetén max. 1 kilóbájtnyi. Sok MCUban megtalálható, de nem mindben. Például az ESP8266-ban nincs, ezért emulálják. Létezik különálló, szerelhető modulja is, ebben az esetben az írási sebessége csökken a használt kommunikációs csatorna sebessége miatt.
**SPI Flash**: Nem felejtő, fájlrendszer memória. Az EEPROMnál kevésbé megbízható, lassabb memória terület. Általában 10.000 írási ciklust bír ki. Cserében olcsóbb, így nagyobb méretben szokták szerelni. Lapított memória terület, azaz könyvtárak létrehozására nincs lehetőség, csak fájlokra. Persze bizonyos esetekben van rá megoldás, de ez egy másik bejegyzés témája. ESP8266 esetében az SPIFFS lib segíti a használatát, ami az SPI Flash File System rövidítése. Legtöbbször a panelon található flash memória, nem a CPU része.
**PINek**: Ezek a lábak. Ezekre vannak kivezetve a különböző funkciók ki és bemenetei. Speciális lábak közé tartoznak például a GND jelzésű földelési lábak. Hibásan GPIOként is szoktak rájuk sokszor hivatkozni, főleg aliexpressen. Ezt csak azért írom, mert lesznek később olyan vackok, amiket csak így fogsz tudni megtalálni alin.

Persze a memóriák közül nem minden feltétlenül az MCU része, van, ami a modulon található. Ilyen pl a NodeMCU esetében a SPI Flash magán a modulon található, nem az ESP8266 MCU belsejében. Hasonló egyértelműen egy SDCard is lehet, mint memória. A foglalat a panelen található, nem az MCU része.

Tehát fontos tudni, hogy a legtöbb ismert modul egy-egy nagyobb MCU család különböző tagjait hordozzák magukon. Ezek közül kiemelnék pár...
### Ismertebb MCUk és paneljeik
#### ATMega328

| ![Arduino UNO klón, kivehető ATMega328PU MCUval](/docs/assets/ArduinoUno_R3_Front.jpg) | 
|:--:| 
| *Arduino UNO klón, kivehető ATMega328PU MCUval* |

Az Arduino UNO-k és Nano-k magja. 8-bites MCU, 5V az alap feszültség, amivel működnek a lábai. A megjelenésével, és jól megtervezett fejlesztési támogatásával az MCUk elterjedésének a legnagyobbat robbanó alapköveit tették le a készítői.

#### ESP8266

| ![NodeMCU ESP8266 MCUval](/docs/assets/NodeMCU_DEVKIT_1.0.jpg) | 
|:--:| 
| *NodeMCU ESP8266 MCUval* |

A legismertebb, legjobban támogatott, és legelterjedtebb Wifi-t használó MCU. Egyszerű vele vezeték nélküli kommunikációra képes eszközöket építeni. A legtöbb Wifis okosotthon eszközben ez található, mint pl. Sonoff relék. A legjobban használható modulja (Development Board - fejlesztői modul) talán a NodeMCU. Ugyanúgy kódolható és használható, mint bármelyik Arduino, egy nagyon fontos különbséggel. Ez 3.3Vos modul, azaz annyival működnek a pinek. Áramellátása mehet nagyobb feszültségről, de a lábakra vigyázzunk! Csak emulált EEPROM van benne, amit az SPIFFS területből hasít le a bootloadere.

#### ESP32

| ![ESP32 Development Board WROOM-32 verziójú MCUval](/docs/assets/esp32.jpg) | 
|:--:| 
| *ESP32 Development Board WROOM-32 verziójú MCUval* |

Az ESP8266 nagytestvére. Rengeteg különböző kivitelben gyártották, mert relatíve erős hardverrel rendelkezik, így sok beépített/ráépített alkatrésszel lehet szállítani. Van RF, LCD, OLED, Camera dev boardja is. Rengeteg lábbal rendelkezik.

#### STM32 család

| ![STM32F103RC8T6 MCUval szerelt Arduino Nano szélességű development board](/docs/assets/stm32-bluepill.jpg) | 
|:--:| 
| *STM32F103RC8T6 MCUval szerelt Arduino Nano szélességű development board* |

Több MCUt magában foglaló család. Sok STM32 alapú fejlesztői panelt az Arduinok méretei alapján készítenek. Hasonló kalakítású dev boardokon találhatók meg, mint az Arduino, de sokkal fejlettebb kivitelben. Alapból 32-bites ARM magról van szó, és olyan más IO pin vezérlésekkel rendelkezik, mint pl. az autókban/repülőkben található CANBus. Ipari környezetben nagyon jól megállják a helyüket az ipari vezérlés területén.

#### ATTiny család

| ![ATTiny85 MCUk és hozzá tartozó USB development boardok](/docs/assets/attiny-programmer.jpg) | 
|:--:| 
| *ATTiny85 MCUk és hozzá tartozó USB development boardok* |

Sok kis formátumú és kis méretű MCUt tartalmazó család. 8-10-14 lábbal, és ATMega/Arduino alapokkal rendelkeznek. Nem nagyon van development boardjuk, ugyanis egyéni, board nélküli feladatok ellátására találták ki őket. Fontos a pici méret, és az Arduino C++ támogatása. Sok projektben teljesen elegek, ahol csak egyszerű áramköröket kell megtámogatniuk. Arduinoval, vagy ISP programmerrel kódolhatók.

#### Persze meg még millió, meg egy...

Rengeteg más MCU létezik hála az égnek. Minden célra már gyártanak hardvert. Kezdve a hihetetlenül kis méretet célzóktól a gépi tanulási módszerekhez, és AIhoz, mesterséges intelligenciához kifejlesztett modellekig. Ismertebbek az FPGA alapúak, melyek teljesen elszakadnak a CPUval, központi számító egységgel rendelkező MCUk világától, és sokkal gyorsabb párhuzamos feladatmegoldást tesznek lehetővé, megnyitva a világot a kezdők előtt a neurális hálózatok, és gépi tanulási módszerek felé.
Ezen kívül a PIC MCUk, melyek sokkal-sokkal megelőzték az Arduinok által kiváltott robbanást, csak sok olyan hardver limitációval rendelkeznek, ami a kezdőknek nagyon nehéz volt kezelni. Ennek ellenére még az ATMegákhoz, ATTinykhoz képest is sokkal jobb energiafelhasználással rendelkeznek, így akkumulátoros, elemes környezetben jön ki szépen az előnyük.
Több olyan is létezik, melyek a robotok világát, esetleg a CNC világot, vagy a rádió frekvenciás kommunikáció támogatására lettek kifejlesztve. Ami a hasonlóság ezek között, hogy legtöbbet igyekeznek úgy kialakítani, hogy az Arduino által lassan iparági szabvánnyá váló környezetben is lehessen kódolni őket C++ nyelven, a saját fejlesztői nyelvük mellett, hogy könnyű legyen az embereket elcsábítani a saját termékük felé.

### Konklúzió

Kezdőknek 2 boardot, és melléjük 2 MCUt ajánlok. Vegyél egy Arduino UNO kompatibilis boardot, mert ezzel képes leszel mind ATMega328, mind pedig ATTiny MCUkat programozni. A lényeg, hogy cserélhető legyen benne az ATMega328 MCU.
Ezek alapján pár darab ATMega328PU (figyelni kell Alin a leírásban, hogy van e rajta Arduino kompatibilis bootloader. Az U betű elméletileg ezt jelenti náluk. De ez már a következő post témája lesz) MCUt mindenféleképpen érdemes beszerezni, mert ha félre kell rakni a projektet, csak kicseréled az MCUt, és van egy új boardod.
A másik MCU pedig egy ATTiny85 legyen. Ezzel meg tudod tanulni a teljes ATTiny család kódolását, és picike, így mini projektekbe tökéletes a 8 kis lábával.
A másik board pedig egy NodeMCU. Ebből olyat vegyél, amit leírtam a bevásárló listás posztom [1. rész](./2020-01-24-hobbielektronika1.md)ében. Tök jó kis dev board, a wifi alapokra, MQTTre, Mash hálózatok alapjainak a megismerésére teljesen jól használható, és baromi egyszerű kódolni.
STM32, és ESP32 boardokat kezdőknek azért nem ajánlom, mert nagyon komplexek. Nagy a tudásuk, és könnyű az elején eltévedni a lehetőségekben és a kód komplexitásukban. Majd, ha már úgy érzed, hogy kinőtted az ESP8266 és Arduino korlátait, akkor jöhetnek számításba. De ez már a jövő zenéje! A következő témám a programozásukról fog szólni.

#### Kudo

Szeretném megköszönni a Hobbielektronika Facebook csoportban lévő tagoknak, akik segítettek pontosítani, így még hasznosabbá tenni ezt a posztot! Örök hála érte!
### Pár hasznos link
[NodeMCU documentáció](https://nodemcu.readthedocs.io/en/master/)  
[Arduino hivatalos oldala](https://www.arduino.cc/)  
[ESP8266 modulok összehasonlító táblázata](https://blog.squix.org/2015/03/esp8266-module-comparison-esp-01-esp-05.html)  
[ESP32 csipek összehasonlító táblázata](https://www.gridconnect.com/pages/espressif-product-comparison)  
[ESP32 boardok összehasonlító táblázata](https://makeradvisor.com/esp32-development-boards-review-comparison/)  
[STM32 MCUk összehasonlító táblázata, klikkelni kell tovább az adott családon](https://www.st.com/en/microcontrollers-microprocessors/stm32-32-bit-arm-cortex-mcus.html)  
[ATTiny család összehasonlító táblázata](https://en.wikipedia.org/wiki/ATtiny_microcontroller_comparison_chart)  
[ATTiny programozása Aruino UNOval (Nanoval is lehet, kb tök ugyanez) 4 perc alatt](https://youtu.be/AmpHIHM41Hw) (a leírásban részletes step-by-step blogbejegyzésre van link)
### Vásárlás
[Arduino UNO klón](https://s.click.aliexpress.com/e/_AsFlCa)  
[NodeMCU (csak CP2102)](https://s.click.aliexpress.com/e/_dZEmNhL)  
[ATTiny85 10db](https://s.click.aliexpress.com/e/_dXOKi5f)  
[ATMega328PU 2db](https://s.click.aliexpress.com/e/_99h9kw)  