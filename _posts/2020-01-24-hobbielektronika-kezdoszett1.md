---
layout: post
author: montyx
---
## Hobbielektronika - részemről ajánlott kezdő szett (Part 1)

Sziasztok!
Alig több, mint fél éve hobbiim közé bekerült az elektronika. Mai napig nagyon élvezem és hasznosnak tartom. A fő vonal, amivel foglalkozom az okos otthon témája, így eköré építettem fel a "raktáramat".
Az Aliexpress lett a barátom, rengeteg mindent be lehet náluk szerezni nagyon olcsón. Persze sokat kell várni, de még mindig megéri. Sikerült is felhalmozni minden baromságot, amit azóta megbántam, így másoknak szeretnék segíteni ezzel a listával, melyet több részre fogok osztani előrehaladás szerint.
Fontos! Ez nem egy ultimate lista! Ez csak az én véleményem. Ha van jobb ötleted, oszd meg kommentben itt, vagy a hobbielektronika facebook csoportban velem!

Kezdetek
Több részre osztom a kezdeti ajánlott dolgokat, mindent igyekszem meg is indokolni.
### Eszközök
Az elején nagyon fontos, hogy ne eye-candyzzünk. Ne vegyünk meg minden vackot, mert csak pénzt égetünk.
1. Multiméter - A legfontosabb. Enélkül bele se vágjunk az egészbe! Az elektromosság kezelése és megértése képtelenség egy használható multiméter nélkül. Én egy elég drágának számító Uni-t multit vettem, ma már nem venném. A következőt ajánlom kezdőknek:
[Multiméter](https://www.aliexpress.com/item/32839539223.html)
Ami miatt jó, hogy olcsó, automata, és tud hőmérsékletet mérni. Ez főleg majd forrasztáskor lesz hasznos, ha nincs, vagy nem megbízható a páka hőmérője.
2. Breadboard - A kezdetek legjobb társa. Kis fehér műanyag tábla, amin lehet dugdosni kábeleket, ellenállásokat, LEDeket, és ICket össze vissza pár jumper kábellel. Nekem már van több breadboardom, de szinte sose elég az elején. Van sok félbehagyott projektem, ahol alkatrészre várok, és nem akartam szétszedni, hogy ne vesszen el a tudás :D
Amit ajánlok, az egy csomag. Van benne egy nagy, két közepes és hat db kicsi breadboard. Ebből el tudod majd dönteni, hogy később melyikből lesz többre szükséged:
[Breadboard](https://www.aliexpress.com/item/32980025688.html)
3. Kezdő kit - Sokat átnéztem már az Alin, ki is próbáltam, de ez vált be a legjobban. Minimalista, minden darabja jól használható, és nem veszünk vele feleslegesen dolgokat:
[Starter kit](https://www.aliexpress.com/item/32871198519.html)
4. Breadboard táp - Az előző kitben található a legjobb kapható breadboard táp. Ami fontos, hogy fekete és tömzsi. Van fehér és piros vékonyka táp is, de azok ipari hulladékok ehhez képest. Ha tápot veszel csak a feketét vedd. Tud 3.3V-ot és 5V-ot is. Kapcsolható. Egy breadboardon akár mindkettő jelen lehet egyszerre:
[Táp](https://www.aliexpress.com/item/32785972837.html)
5. Áramforrás - Ez egy elég komplex téma. Most próbálok a lényegre összpontosítani. Marha sok áramforrásom van. Feleslegesen a legtöbb. Amit a legtöbbet használok, az 4db vapelésből visszamaradt 18650es cella, és hozzá egy műanyag 4x-es foglalat. Szépen sorba vannak kötve benne a cellák, és mindegyikről van leállás. Így képes leadni 3,7V/7,4V/11,1V/14,8V-okat. Attól függ, hogy melyik leállást használom.
NAGYON FONTOS! Ne terheld! Ez tényleg csak vizsgálathoz jó. Nagyobb fogyasztók, mint villanymotor, erősebb izzó simán kinyírja a cellákat. Én leggyakrabban a breadboard meghajtására használom 2S állásban, azaz a második cella után leállva, és a breadboard fekete kis tápjába bedugva:
[18650 foglalat](https://www.aliexpress.com/item/33037738446.html)
Persze lehet ugyanilyet kapni, ami AA, vagy AAA elemekkel működik. Ha nincs otthon egy jó és megbízható 18650 töltőd, akkor ajánlom az Xtar termékeket, vagy vegyél inkább elemes megoldást.
6. Szike - A valaha vett legértékesebb olcsó vackom. Nap mint nap használom, és nem tudom hogy tudtam eddig élni nélküle. Mindent ezzel bontok ki. Használtam már csavarhúzónak, IC kiszedőnek, blankolni kábelt, szétszedni telefont, formázni akrilt, meg még rengeteg, rengeteg más dologra. Mindig kéznél van. Van egy rakat színben, nekem a lila a kedvencem, mert a kuplerájban is mindig látszik:
[Szike](https://www.aliexpress.com/item/4000271778571.html)
7. Műszerészfogó - Must have! Mindenre is jó, pont mint a szike. Nagyon szép és precíz vágásokat lehet vele csinálni. Nekem kettő is van, a biztonság kedvéért:
[Műszerész fogó](https://www.aliexpress.com/item/4000072783520.html)
8. Mini fogók - Nem részletezném, marha hasznosak. Nekem ami bevált az a rövidebb egyenes kúp, a ferde kúp, a sima lapos fogó:
[Mini fogók](https://www.aliexpress.com/item/32882361240.html)
9. USB HUB - A legjobb PC-s kiegészítőm. Marha sok USBre van szükségem, és ez mindent ellát egyszerre:
[USB HUB](https://www.tp-link.com/hu/home-networking/computer-accessory/uh720/)

Ezekkel a műszerekkel, és szerszámokkal tökéletesen el lehet kezdeni dolgozni, és ismerkedni az IoT és hobbielektronika világával.
Jöjjenek a

### Alkatrészek
1. NodeMCU - talán a legfontosabb, és legtöbbet használt cuccom. Ugyanazt tudja nagyjából, mint egy Arduino Nano, cserébe van benne Wifi is. Ugyanúgy programozható, mint az Arduino, ugyanazok a libraryk használhatók vele, és a PINjei is nagyjából hasonló tudással, persze más kiosztással rendelkeznek. Tökéletes kis masina, én csak ezt ajánlom kezdésnek, mert nem kell egyből nekirohanni a Wifi világnak, anélkül is használható, mint egy sima Arduino.
FONTOS! Három fontos dolog van, amit tudni érdemes róla. Az első, hogy csak v1.0, vagy más néven rev. 2 eszközt vegyünk. A v0.9, vagy rev 1.x eszközök egyszerűen nem férnek rá egy breadboardra. Rengeteg fejfájást meg lehet vele spórolni. A másik fontos dolog, hogy ez az Arduinokkal szemben nem 5V PINekkel rendelkezik, hanem csak 3.3V a ki és bemenete. Figyeljünk erre oda, nekem eddig az esetek 90%-ban egyszerűbb volt ezzel az életem, mintha 5V lett volna. A harmadik pedig, hogy csak olyat vegyünk, amin CP2102 soros chip van. Ezt ránézésre onnan lehet tudni, hogy a mikro USB mellett látható csip négyzet alakú tokkal, vagy kétoldali hosszúkás tokkal rendelkezik. A négyzet a jó, megbízható, a CH340G, azaz a hosszú elég instabil.
Érdemes 2-3 ilyet beszerezni, mert marha olcsó, és jól támogatott:
[ESP8266](https://www.aliexpress.com/item/32965931916.html)
2. Power kit - Ez bőven elég kezdeni. Minden van benne az elején, nem kell boltokba rohangálni. Van benne ellenállás, kondenzátor, dióda, LED, stb. Mindegyik olyan méretű, ami hasznos egy kis áramkör összerakásához:
[Power kit](https://www.aliexpress.com/item/33000795485.html)
3. Potméterek - Ez is egy kit. Minden méret van benne, ami eddig kellett nekem:
[Potik](https://www.aliexpress.com/item/4000106237193.html)
4. Rotary encoder module - egy már előre felszerelt modul. Arra jó, hogy megtanulja az ember, hogy mi a különbség a poti és a rotary encoder között:
[Rotary](https://www.aliexpress.com/item/32392018473.html)
5. Szenzorok - Na itt tud elszállni az ember agya. Van millió egy fajta. Ebbe nem is szólnék bele, döntsd el, hogy téged mi érdekel. Ezért inkább egy megbízható boltot ajánlanék, ahol fasza szenzorokat lehet kapni:
[Shop](https://www.aliexpress.com/store/group/Sensor/1678083_509516053.html)
6. Csatlakozók/kábelek - Ezeket azért érdemes beszerezni, mert ugye el kell juttatni az áramot a breadboardig, fel kell tudni kódolni a NodeMCUt, meg hasonlók. Kezdjük azzal, ami az elem/aksi tartóhoz fog kelleni, meg a breadboard táphoz:
[5,5x2,1 csatik](https://www.aliexpress.com/item/32990462283.html)
Következő az USB kábel a NodeMCUhoz. FONTOS! Legyen benne adatkábel. Sok olcsóban nincs, csak töltőnek használható. Érdemes három fajtát tartani otthon. Mini, micro, és sima. Esetleg egy USB-C is jól fog majd jönni, de az ráér. Csak egy-egy példa:
[Mini USB](https://www.aliexpress.com/item/32826618241.html)
[Type A USB-USB](https://www.aliexpress.com/item/32666322698.html)
7. 555 - Ez legyen az első kezdő Integrated Circuitod, azaz IC-d. Egy timer. Tanuld meg, hogy lehet vele LEDeket vezérelni. Ha ezt érted, akkor az összes többi IC menni fog. Foglalattal használd, ne az IC lábait vágd agyon:
[555](https://www.aliexpress.com/item/32906115330.html)
8. Attiny - Ez az Arduino IC-jének a kistestvére. Programozható ez is, csak kell kis ügyeskedés hozzá. Pont ezért érdemes megismerni, hogy lássa az ember hogyan működik egy Microcontroller, azaz MC. Előbb érdemes a development boarddal használni, azután pedig anélkül. Ami fontos, hogy PU végüt vegyünk mindegyik Attiny chipből, mert azon van bootloader gyárilag. Anélkül nagy szívás:
[Attiny Programmer](https://www.aliexpress.com/item/4000449525756.html)
[Attiny 45 és 85](https://s.click.aliexpress.com/e/_98PdF4)
9. Kijelzők - Ugye egyrészt látni szeretnéd, hogy mi történik a kis világodban, másrészt azért, mert sokat lehet belőle tanulni. 2 fontos kijelző típust fogok linkelni. Az egyik SPI, a másik I2C kapcsolattal rendelkezik. Ezeket érdemes első körben megtanulni, hogy mi a különbség.
I2C:
[LCD1602](https://www.aliexpress.com/item/32988862895.html)
[0.91 inch OLED](https://www.aliexpress.com/item/32946734550.html)
[0.96 inch OLED](https://www.aliexpress.com/item/32920071528.html)
[SPI touch screen](https://s.click.aliexpress.com/e/_9AksGa)
10.  Gombok - Csak hogy legyen mit nyomkodni:
[Nyomógombok](https://s.click.aliexpress.com/e/_A0bOnu)
12. Óra modul - Nagyon jó kísérletezni egy órával. Alább írok majd egy RTC modult hozzá:
[7 Szegmenses LED - TM1637](https://www.aliexpress.com/item/1961805015.html)

### Egyebek
Ezeket csak ajánlom, egyik se must have. Vagy jók kísérletezni és tanulni, vagy pedig hasznosak ezért-azért.

1. ESP32 - Remélhetőleg hamar kinövöd a NodeMCU kereteit. A következő lépésnek a nagytestvért, az ESP32-t ajánlom. Fontos, hogy több verziója is van. Ezekről lehet találni leírást. Én ezt szeretem használni, tudni kell, hogy breadboardra nem fér fel:
[ESP32](https://www.aliexpress.com/item/33053140589.html)
2. Dummy load ellenállás - Arra jó, hogy beterhelj vele valamit, ha épp nincs kéznél valami fogyasztó:
[Dummy load](https://s.click.aliexpress.com/e/_AlkNcm)
3. Mágnesek - Nagyon jók például, ha rögzíteni kell valamit, vagy csavarhúzóra, hogy ki tudj venni vele egy csavart:
[Mágnesek](https://s.click.aliexpress.com/e/_AZzT7G)
4. RTC module - Real Time Clock modul. Arra jó, hogy megjegyzi az időt akkor is, ha éppen nincs áram alatt az áramkör. Meg persze rakat minden másra:
[RTC](https://www.aliexpress.com/item/32533518502.html)
5. Relé modul - Kérlek ne használd nagyfeszültség kapcsolására, amíg nem vagy biztos benne mit csinálsz. Meg tud ölni! Sima egyenáram, kisfeszültség kapcsolására marha jó. Tanulni pl egy LEDet kapcsolni vele, vagy egy kis villanymotorot, szervót.
[Relé modul](https://www.aliexpress.com/item/33036926367.html)
6. Boost converter - Feszültség növelő. Tanulni lehet vele a feszültség szabályozást. Direkt kijelzőset raktam be, mert azzal könnyebb bánni:
[Boost converter](https://www.aliexpress.com/item/32294852872.html)
7. Buck converter - Az előző teljesen megegyező ellentéte. Feszültség csökkentő:
[Buck converter](https://www.aliexpress.com/item/32800211016.html)
8. LED mátrix - Nagyon jól meg lehet vele tanulni a mátrix vezérlést. Fényújságnak, és állandó kijelzőnek, meg minden másra is jó lehet. Csak a képzelet szab határt:
[LED mátrix](https://www.aliexpress.com/item/32841678065.html)
9. Mini szervó - Egy mini szervó mindig jól jön. Jó páros egy rotary encoderrel. Pozícionálást lehet vele tanulni:
[Mini szervó](https://www.aliexpress.com/item/32975618090.html)
10. Mini szervó vezérlő - Próbáld ki a szervót MC nélkül is:
[Szervó vezérlő](https://www.aliexpress.com/item/4000147360365.html)
11. Mini elektromotor - Nem vágod vele agyon az áramforrást, olyan pici. A PWM és fordulat szabályzás tanulására nagyon jó:
[Elektromotor](https://www.aliexpress.com/item/32664796912.html)
12. Mini PWM speed controller - Mini motorhoz mini vezérlő. Ez is hasznos, hogy előbb MC nélkül vezéreld a motort:
[PWM controller](https://www.aliexpress.com/item/33045121306.html)
13. Transistor pack - Ezzel lépsz be a modern fizika világába. Ezzel kezdődött a modern számítógép korszaka. Alaptudás, ebben a kitben benne van minden alap tranyó:
[Tranzisztorok](https://www.aliexpress.com/item/32856312651.html)
14. BJT és MOSFET - Ezeket megértéshez ajánlom. Rakok is hozzá egy fasza magyarázó tutorialt:

[Darlington](https://s.click.aliexpress.com/e/_AOwXoO)

[MOSFET IRF520](https://s.click.aliexpress.com/e/_AUqf1o)

[BJT 2N2222](https://s.click.aliexpress.com/e/_A7uYrY)

[Tutorial1](https://dronebotworkshop.com/transistors-mosfets/)

[Tutorial2](https://www.instructables.com/Transistor-Basics-BJTs/)

No a végére pár gondolat. Ez egy hosszú lista. Nagyjából próbáltam fontossági sorrendben leírni a dolgokat. Ne vegyél meg persze egyből mindent, de ahogy haladsz tudásban, haladhatsz a listával is. Az eszközök és alkatrészek listák nagy részét sajnos már a legelején érdemes beszerezni, különben vagy itthon veszed meg ugyanazt a kínai csodát 5-10x-es áron (tapasztalat, hidd el. pl multimeter át van logózva, és 6x annyiba kerül), vagy pedig ülsz otthon heteket, és várod, hogy megjöjjön a hiányzó alkatrész. A egyebek lista pedig azért lesz majd fontos, hogy lépésenként megértsd az alapokat. Legyen mivel tutorialokat csinálni, és tanulni.
Remélem hasznos a lista, minden tanácsot szívesen veszek.
A következő részben már egy kicsit fejlettebb dolgokról fogok írni, mint pl. forrasztás, NYÁK készítés házilag, tápok, és egyéb, kicsit már advanced eszközökről, alkatrészekről. Addig is szép napot, jó kísérletezést!
Ja igen! Kérdezz sokat! Ajánlom erre a Hobbielektronika facebook csoportot. A legkirályabb emberek vannak ott, nagyon segítőkészek. Ne feledd, nincs hülye kérdés!