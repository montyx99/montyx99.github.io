---
title: 3D printing - Stepper motor (Alapozó)
layout: post
author: montyx
categories: 3d-printing
tags: stepper motor steppermotor nema17 3d-printing 3d-printer
---
Feljött a 3D nyomtató csoportunkban, hogy miben különbözik két stepper motor. Gondoltam, ha már nekik összefoglaltam azt, ahogy én tudom, akkor leírom ide is. Előre szólok, hogy ez a jelenlegi legjobb tudásom, remélem nagyban nem tér el a valóságtól.

### Adatlapok
Nagy általánosságban elmondható, hogy minden stepper motor típusnak fellelhető a neten az adatlapja. Ha a kedves gyártó a motor aljára olyan típusszámot tűntet fel, amiről nem találsz google segítségével "datasheet"-et, akkor az egy átcímkézett motor lesz és valószínűleg a legáltalánosabb, legelterjedtebb motort használja, amit a többiek is. Pl. normál cartesian elrendezésű nyomtatóknál, mint Artillery Genius, vagy SideWinder 17HS4401 motorokat szereltek a tengelyek mozgatására. 

A stepper motorok esetében nekem a legfontosabb érték kiválasztás esetén a nyomaték. Ebből kétfajta létezik, a Holding Torque és a Detent Torque. Az első adja magát, az azaz érték, amellyel a motor álló helyzetben tudja tartani a rá érkező forgató erőket akkor, amikor a tekercsek áram alatt vannak. A második, a detent torque pedig az a nyomaték, amivel akkor tudja tartani a tengelyt, amikor nincs áram alatt egyik tekercs sem, pl. amikor áramtalanítva lett a gép, amelynek a motor egy alkatrésze. Ez utóbbit lehet akkor érezni, amikor a motor tengelyét kézzel forgatja az ember.
A Holding Torque érték az, ami az igazán nagy előnye egy stepper motornak egy hagyományos DC szervó motorral szemben. Ezért választjuk a stepper motort akkor, ha valamekkora tömeget kell pontos pozícióban tartani, pl. 3D nyomtatók esetén. 

Ezen kívül a forgási nyomaték is fontos. Ez az a nyomaték, amit a motor kifejt mozgatás közben. Ez a Holding Torque - 2 x Detent Torque képlettel írható le alacsony forgási sebesség esetén, mivel a motor saját belső nyomatéka ellen kell dolgoznia a tartó nyomatéknak. Általában tehát kimondható, hogy a Holding Torque érték minél magasabb egy motor esetén, annál erősebb az adott motor. Ennek persze ára van, de ne szaladjunk előre. Vegyünk egy példa adatlapot.



| ![MotionKing 17HS család - adatlap](/docs/assets/20230205-stepper-17HS-series-datasheet.png) | 
|:--:| 
| *MotionKing 17HS család - adatlap* |

Az adatlapról leolvasható fontosabb értékek:
1. Step angle: mekkora szögtávolságot megy a motor 2 lépés között. ez általában 1.8 fok. van 0.9-es is, de azt csak ritkán használják.
2. Rated Current A: ez a max áramerő. ennek 70-80%-ára szoktuk állítani az áramerőt Klipperben. Ez az áramerősség szükséges ahhoz, hogy forduljon a tengely 1.8 fokot.
3. Phase Resistant: ez hibakeresés során is fontos, mert ez alapján lehet kimérni az egyes fázisokban van e rövidzár. Illetve ettől is függ, mennyire melegedhet normál működés közben a motor. nagyobb ellenállás érték mellett jobban melegszik, mert többet fűt el az áramból a motor működés közben.
4. Phase Inductance: indukció fázisonként, szintén hibakeresés során mérhető. Később még szó lesz róla.
5. Holding és Detent torque: ezek a nyomatékok. Minél nagyobb annál erősebb a motor.
6. Inertia: a tengelyen lévő tömeg által kifejtett erő T = F * r. Itt F = M * A, ahol az M a tárgy tömege, az A a gyorsulás. Maga a tömeg által kifejtett erő határozza meg az inerciát, amivel forgatva a tengelyt adott szög esetén fellép az adott nyomaték. Mivel egy hagyományos 3D nyomtató kis teljesítményűnek számít a komolyabb CNC megmunkáló eszközökhöz képest, így keveset szoktak ezzel az értékkel foglalkozni normál nyomtatók esetén.
7. Lead wire: 4 - bipolar, 6 - unipolar
8. Motor weight: motor tömege. Általánosságban kimondható, hogy azonos gyártó, azonos sorozata esetén minél erősebb egy motor, annál nehezebb.

Ezek után jön bal alul egy rajz, ahol fel van minden érték tűntetve a fizikai méretekről, kivéve a hosszt. Az adott stepper motor sorozatot a fizikai méretek határoznak meg. Esetünkben a sorozat neve a 17HS azt jelenti, hogy nagyjából 1.7" a motor mérete mindkét méretében. A motor faceplate-je, azaz a tengely irányába mutatott felülete 1.7" x 1.7", azaz durván 42mm x 42mm.

A jobb alsó táblázatban van az utolsó fizikai méret táblázata, azaz a hossztábla. Ettől változik a névben a 17HS sorozatnevet követő szám. Tehát egy 17HS4401 esetében ez pontosan 40mm-ert jelent, mert csak azt kell nézni, hogy 17HS4. A 17HS8401 esetében pedig 48mm ez a hossz. Ettől függ a tekercsméret. minél hosszabb egy motor, annál hosszabb tekercstartó fér bele, amin annál hosszabb lesz a feltekercselt vezetékek hossza fázisonként. Illetve ezen múlik mekkora mágnest szerelhetnek bele. Így erősebb lesz a motor és persze várhatóan nagyobb az ellenállása azonos minőségű vezetékek használata esetén.

Általánosságban elmondható, hogy a hagyományos gyártók, beleértve a kínaiakat, ezektől az értékektől nagyban nem térnek el. Azaz két 17HS4401 motor általában gyártótól függetlenül azonos értékeken működik. Ennek ellenére lehet egy LDO motorra 1.8A van írva, de ők tudják, hogy mivel jobb minőségű és nagyobb tisztaságú anyagból készítik a vezetékeiket, így mehetne rá nagyobb áramerő is. Ezzel viszont növelik a motorjaik élettartamát és megbízhatóbbak lesznek a motorjaik, mert nagyjából minden esetben elmondható a DC árammal működő gépek esetében, hogy minél jobban megközelíted valamely fizikai határértékét egy adott áramköri elemnek, annál hamarabb öregszik és annál hamarabb deglik meg.
Szintén LDO esetén igaz lehet az is, hogy mondjuk erősebb mágneseket használ, így ugyanakkora nyomaték eléréséhez elég kevesebb áramerősségre van szüksége. Illetve természetesen nagyobb lehet az adott motor hőtűrése is, azaz magasabb hőmérsékleten képes üzemelni probléma nélkül.

A fenti adatlapot tartalmazó teljes katalógust az új P/N számokkal [innen](/docs/reference/HB_Stepper_Motor_E.pdf) tudod letölteni (Kudo: MotionKing).

### Indukció

Akkor térjünk vissza kicsit az indukcióra. Egész pontosan a fenti felsorolásban a 4-es ponthoz egy kis kiegészítés: az indukció mutatja meg azt, hogy a fázisra adott áramerősség maximális méretét mikor érheti el a fázis. Minden fázis egy tekercs, és így van egy indukciós értéke, ami azt jelenti kb., hogy fel kell töltődnie, mint egy kondinak. tehát szépen elkezd növekedni a tekercsben a töltés és amikor az maxol, akkor éri el a teljes tekercs a kívánt áramerő értéket és forgat úgy, ahogy akkora áramerőn kellene. ha egy motor esetében a fázis feszültség 2.5V, akkor azt egy képlet alapján kiszámolható az feszültségből, az ellenállásból és az indukcióból, hogy mennyi idő alatt töltődik fel ilyen indukciós érték mellett a tekercs és akkor fordul a motor 1.8 fokot.

| ![Áramerő 2.5V feszültség esetén az idő függvényében](/docs/assets/20230205-stepper-aramero-ido-fuggveny.jpg) | 
|:--:| 
| *Áramerő 2.5V feszültség esetén az idő függvényében* |

Az ábrán látható görbe megmutatja, hogy a vizsgált motor esetében 2.5V feszültség esetén a fázis tekercs kb. 10 ms alatt éri el a szükséges 5A 90%-át, míg 16 ms alatt annak a 98%-át. Ekkor fordul 1.8 fokot a motor. na ez viszont azt jelenti, hogy a teljes körfordulat 200 lépését (360/1.8 fok) kb 3.2 másodperc alatt éri el. ami ugye azt jelentené, hogy használhatatlanul lassú lenne a motor.
Itt jön közbe a az úgynevezett buszfeszültség. Azaz a rendszered milyen feszültség értéken dolgozik. Elterjedt a 12V-os és a 24V-os rendszer a nyomtatókban. Persze erősebb motor driverekkel, mint pl. TMC5160-as ennél jóval magasabb értéken is lehet működtetni.

| ![Fenti grafikon feszültség eltérés esetén](/docs/assets/20230205-stepper-aramero-ido-fuggveny-feszultseg.jpg)   | 
|:--:| 
| *Fenti grafikon feszültség eltérés esetén* |

Minél nagyobb a buszfeszültség, annál hamarabb töltődik fel a tekercs. 5V esetén a 90%-ot, azaz 4.5A-t cca 4, míg 25V esetén cca 1 millisecond alatt éri el a motor fázis tekercse. Ezzel már rendesen lehet pörgetni a motort. Persze a feszültség növelésével nő a rezonancia és az elfűtött hő mennyisége is, de a forrásom szerint ökölszabályként kimondható, hogy egy rendes motor a megadott fázis feszültsége x 10-24 buszfeszültség használható, azaz mondjuk 2V fázis mellett 20-48V a maximum használható buszfeszültség a rendszer és a motor veszélyeztetése nélkül.

Nagyjából ennyire gondoltam, hogy megosztok a témával kapcsolatban. Ha kérdés merülne fel, akkor megtalálsz a Telegram csatornánkon: [Telegram csoport](https://t.me/+ALE1Kya1HFpiNjRk)

### Kudo
[MotionKing](http://www.motionking.com/search_c.asp)  
[Elinko International JPC](https://www.e-jpc.com/stepper-motor-voltage-explained/)  
[Novanta IMS](https://novantaims.com/application-note/calculating-inertia-sizing-stepper-motors/)

### Beszerzési linkek
[Mellow LDO extruder motor](https://s.click.aliexpress.com/e/_DkRJGwH)  
[Mellow MOONS 48mm hosszú nema17 motor](https://s.click.aliexpress.com/e/_DdGUGqV)  
[Mellow LDO 60mm hosszú nema17 motor](https://s.click.aliexpress.com/e/_DCtGlEt)  
[UsongShine nema17 17HS4401 motor pack](https://s.click.aliexpress.com/e/_DFkW5df)
[StepperOnline nema17 17HS08 extruder pancake motor](https://s.click.aliexpress.com/e/_DkXwvs5)

