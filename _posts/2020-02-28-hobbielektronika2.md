---
title: Hobbielektronika - részemről ajánlott kezdő szett (Part 2)
layout: post
author: montyx
categories: electronics
tags: hobbielekronika elektronika szerszámok forrasztó páka ón harmadikkéz ts100 ts80 ts80p
---
Üdv ismét!
Sok víz folyt már le a Dunán, mióta megírtam az első részt. Sok minden vacak megfordult azóta is a kezemben, úgyhogy folytatnám az előző listát. Immáron megpróbálom fotókkal kiegészíteni, hátha az Aliexpresses linkek megdöglenek. Illetve pár dolgot angolul is leírok, vagy csak angolul, ha nem tudom a magyar megfelelőjét. Az angol szavakat azért akarom kiemelni, mert így sok mindent egyszerűbb lesz később Alin keresni.


### Forrasztó páka
Elég sok mindent az Alin úgy lehet megvenni, hogy nincs forrasztva, max az SMD alkatrészek.
Ezek azok, amiknek a lábai a nyomtatott áramkör (tudom, hogy a NYÁK nem pontosan ezt jelenti, de ma már mindenki erre használja, úgyhogy én is így teszek) tetején vannak, nem pedig kis lyukakon keresztül átlógnak a túloldalra. Az utóbbiak a DIP, vagy Through Hole (magyarul talán furatszerelt a helyes kifejezés) alkatrészek.
No tehát forrasztanom kellett sokat. Az öreg motorosok, főleg akiknek az elektronika a szakmájuk azt mondják, hogy bármivel lehet forrasztani. Ez így is van. Én is vettem egy ilyesmi forrasztó pákát (soldering iron)...

| ![Olcsó páka](/docs/assets/electric-welder.webp) | 
|:--:| 
| *Olcsó páka* |

... talán a praktikerben. Működik, lehet vele ezt azt csinálni, de mindenesetre jobb jó vaskos kábelek forrasztásához, mint NYÁK (angolul PCB - printed circuit board) szereléséhez. Persze arra is lehet használni, de kezdőként egy átok tud lenni. Amíg csak ez volt, addig nem is nagyon forrasztgattam.
Jöjjön hát az én kis kitem:

| ![Forrasztó szett](/docs/assets/soldering-kit.jpg) | 
|:--:| 
| *Forrasztó szett* |

Jobb felül, az a picike egy TS80P nevű csoda.
FONTOS!!! QC3.0 (quick charge 3.0), vagy PD2 (Power Delivery 2.0) töltő kell hozzá, így olyan kitben vegyük, ahol adnak hozzá töltő dugaljt, vagy venni kell külön egyet. A QC3.0 esetén 9V 2A, míg PD2.0 esetén 12V 2.5A a maximális felvett áram.  
[TS80P](https://s.click.aliexpress.com/e/_AVHNMm)

Van egy évvel idősebb testvére is a TS100:

| ![TS100](/docs/assets/ts100.jpg) | 
|:--:| 
| *TS100* |


[TS100](https://s.click.aliexpress.com/e/_AnAoeW)
Ez utóbbi kicsit olcsóbb, és 12V-ról működik. Ami fontos, hogy a TS100-hoz olcsóbb a hegy. Sokkal. Cserébe a fogási pontja magasabban van pár centivel, mert a TS80 esetében a rácsot lehet fogni, míg a TS100-nál ugye ott egy hosszú szár. Ne játszuk azt, mint a hülye PR képeken van! :D

Folytassuk a kitet. Ugye a műszerész fogót, ami a képen kékkel van jelölve, már linkeltem az előző részben. A mini forrasztó állványt, szivaccsal kaptam a pákához. Vicces, de ehhez a pici pákához teljesen elég.

### Forrasztó ón
Na ez nagyon nagy szívás tud lenni. Ezeket a tubusos, vagy tollnak is nevezett csőben található ónokat (solder wire), amit bármilyen pákához adnak Alin el kell felejteni. Sajnos az én ónomon nincs meg a papír már, így nem tudtam lefotózni. Rengeteg helyen utánajártam a témának, és ugyan még nem érkezett meg, de sokan ajánlják a Mechanic HX-T100 ónt:  
[MECHANIC ón](https://s.click.aliexpress.com/e/_9i0U3o)

| ![Forrasztó ón](/docs/assets/MECHANIC-55g-Solder-Wire.webp) | 
|:--:| 
| *Forrasztó ón* |

Első körben 55 grammos kiszerelést ajánlok. Ha beválik, úgyis veszel majd többet belőle. Kezdőknek jobb az 1 mm átmérő, mert több benne a folyatószer (flux angolul), illetve kevesebbszer kell átfogni forrasztás közben, amikor elfogy az ón a kezedből. Ha esetleg nem válna be az ón, amikor megjön, akkor le fogom írni ide. Ha már szóba került, akkor jöjjön a flux. [UPDATE] Azóta megérkezett és tényleg ég és föld a hagyományos kínai vackokhoz képest.

### Folyatószerek és ónszívó szalag
A dobozkámban 2 fajtája is van. Az egyik egy toll alakú. Ez egy flux folyadék, ami arra jó, hogy SMD alkatrészeket forrasszon vele az ember, vagy ha elb*szott egy forrasztást, akkor ki tudja szerelni könnyebben az alkatrészt. Ezen kívül mostanában egyre többször találkozom olyan kínai szenzorokkal, ahol nem megfelelő a forrasz szem, és az istennek nem akarja körbefutni az ón a szemet. Ilyenkor is tud segíteni.
FONTOS!!! Alkohollal (orvosi, vagy izopropil alkohol, más néven izopropanol) le kell mosni a végén, mert megmarhatja a felületet. Őszintén megvallom, ennek nem néztem nagyon utána, csak azt vettem, ami a legolcsóbb volt, és sok jó szöveges értékelése volt Alin:  
[Flux pen](https://s.click.aliexpress.com/e/_AS3oQW)

| ![Flux toll](/docs/assets/flux-pen.jpg) | 
|:--:| 
| *Flux toll* |

A kiszereléshez a legolcsóbb megoldás a rézszalag, vagy ónszívó szalag. A lényege, hogy ha véletlenül összeforrasztottál két olyan szemet, amit nem akartál, akkor ezt kell elővenni. Jó rongyosra széthúzgálod, majd a pákával az ónt átmelegíted, miközben hozzáér a szalag. Csak úgy szívni fogja felfelé a felesleges ónt. Kiszerelésnél nagyon-nagyon jól tud jönni. Amíg kezdő vagy, addig úgyse érdemes ónszippantóra költeni. Majd tudni fogod, mikor jön el az ideje. Addig tökéletes lesz ez a szalag. 2-2,5 mm-es szalagot ajánlok. Tudom, hogy nem ez van a dobozkámban, de nincs nagy tudomány benne, így a legolcsóbbak közül érdemes válogatni:  
[Ónszívó szalag](https://s.click.aliexpress.com/e/_AEnNcW)

| ![Ónszívó szalag](/docs/assets/solder-remover-wire.webp) | 
|:--:| 
| *Ónszívó szalag* |

FONTOS!!! Soha ne fogd a szalagot magát, csak a dobozát. Brutál jól vezeti a réz a hőt, így simán hólyagosra tudod égetni a szalaggal a kezedet. Tapasztalatból mondom. :)
A másik folyatószerem olyan dobozban van, mint egy cipőpaszta. Az angol neve flux rosin:  
[Kemény rosin](https://s.click.aliexpress.com/e/_AlU4nu)

| ![Kemény rosin](/docs/assets/hard-rosin.webp) | 
|:--:| 
| *Kemény rosin* |

Ez nem kimondottan a PCB-re való. Bár kis fogpiszkálóval biztos arra is lehet használni, de arra ott a toll. Ezt a páka tisztítására használom forrasztás közben. Marha jó cucc, nagyon bevált ez a márka. Volt több fajtám már, de mindet kidobtam, ezt kivéve. Eszi le a mocskot a páka végéről, ami gyönyörű szép tiszta lesz tőle. Ha már páka tisztítás, jöjjön az utolsó darab a kitből.


### Dörzsi
Réz dörzsi, kis dobozkával. Forrasztás közben ugye az ón közepéből ömlik ki a flux, illetve a pákán is lesz már ón, ami megég. Illetve a páka hegye is elkezdhet elszíneződni kékes feketére. Ez azt jelenti, hogy oxidálódott a külseje. Ekkor kell a fenti kerek dobozos fluxban jól megmeríteni, megdörzsölni utána jól ebben a réz dörzsiben, megint megúsztatni a fluxban, és a mini szivacsban tisztára törölni. Ezt kell ismételgetni párszor, és gyönyörű tiszta lesz a páka hegye.
Fontos, hogy réz legyen, mert akkor nem ragad hozzá, és jól elvezeti a hőt, így biztosan nem olvad meg. Ebben sincs nagy tudomány, olcsó legyen. Ami fontos, hogy először olyat vegyél, aminek van háza, aztán már majd csak utántöltő fog kelleni:  
[Réz dörzsi](https://s.click.aliexpress.com/e/_AU0eWO)

| ![Réz dörzsi](/docs/assets/solder-cleaning-ball.webp) | 
|:--:| 
| *Réz dörzsi* |

### Alátét
No most ugyan pont nincs itthon, de a legjobb cucc az asszony/anyu sütis szilikon lapja. Hullik a forró ón, félregurul a páka, és már ég is az asztal. Ezzel elkerülheted, hogy gond legyen belőle. Lehet kapni sok drágábbnál drágább szervizes szilikon matracot kis lyukakkal, meg dobozkákkal az alkatrészeknek. Tényleg zseniális cuccok, volt már szerencsém hozzá. De halál felesleges az elején. Majd tudni fogod ezt is, hogy mikor szánj rá pénzt. Én pont jól elvagyok a szilikon sütő alátétemmel. Rózsaszín rulez!  
[Szilikon alátét](https://s.click.aliexpress.com/e/_A8RY98)

| ![Szilikon alátét](/docs/assets/silicone-mat.webp) | 
|:--:| 
| *Szilikon alátét* |

### Világítás
A plafon/fali lámpa nem elég. Nem lesz elég, tutira. Kelleni fog legalább egy, de inkább 2 világító eszköz. Elsőnek egy olyan lámpa, ami flexibilis karral rendelkezik. Nekem a legótvarabb IKEAs szürke asztal szélére szerelhető flexi lámpám van. Tökéletes. Mindig oda világítok vele, ahova kell. Pont ez:
TERTIAL Work lamp - IKEA
Flexi karos lámpa
A másik egy LEDes kislámpa, lehetőleg nagyítóval. Lehet fejre szerelt is, sokan szeretik. De fejre szerelhető nagyítót ne vegyél, mert azok sajnos órás szemüveg mind. Annak viszont 1-2 cm a használati távolsága, így teljesen haszontalan. De a fejlámpa az frankó, főleg ha állítható a fényereje.  
[Ledes fejlámpa](https://s.click.aliexpress.com/e/_A21K3g)

| ![Ledes fejlámpa](/docs/assets/head-lamp.webp) | 
|:--:| 
| *Ledes fejlámpa* |

### PCB satu és harmadik kéz

Ugye forrasztás közben mozog össze-vissza a cucc, ahogy hozzáérünk. Lehet persze háztartási dolgokkal lefogni, pl. féltégla, csak vannak olyan kis vackok, hogy mindig gond lesz vele. Érdemes egy PCB tartóra beruházni. Két fajtát is ajánlok, egy nagyon olcsó kezdőt:  
[PCB satu](https://s.click.aliexpress.com/e/_AOh270)

| ![PCB satu](/docs/assets/pcb-clamp01.webp) | 
|:--:| 
| *PCB satu* |

Illetve egy drágább, de tényleg baromi jó cuccot:
[Profibb PCB satu](https://s.click.aliexpress.com/e/_9GBF90)

| ![Profibb PCB satu](/docs/assets/pcb-clamp02.webp) | 
|:--:| 
| *Profibb PCB satu* |

Nekem ez az utóbbi van, de venni fogok egy az olcsóhoz hasonlót is. Az olcsót érdemes egy nehezebb vastag vaslemezre, vagy nehéz keményfára csavarozni, mert különben mozogni fog. Vagy jó lehet még egy csúszásgátló gumi is az aljára. A profibb cucchoz nem kell semmi. Magában is tökéletes. Nagyon szeretem használni, és annyira nem is drága.
A harmadik kéz angolul third hand. Vettem egy ilyet, és azóta is átkozom magam miatta:

| ![Nagyon rossz harmadik kéz](/docs/assets/third-arm01.webp) | 
|:--:| 
| *Nagyon rossz harmadik kéz* |

Jó cucc lenne, ha nem akarna állandóan felborulni. Ha valaki le tudja fúrni a közepével az asztalhoz, akkor a legjobb cucca lesz a világon. Amúgy fos. Ami a lényeg, hogy az alján a fém talp egy kalap szart nem ér. Simán az üres karok eldöntik az egész hóbelevancot állandó jelleggel.
Sajnos nincs vele tapasztalatom, de ha ma vennék, akkor ezek közül választanék, kérlek ne nézd az árakat, csak a kivitelt. Mindenütt elmagyarázom miért tetszik, és válogathatsz magadnak Alin.  
[Fasza harmadik kéz](https://s.click.aliexpress.com/e/_AsjVoO)

| ![Fasza harmadik kéz](/docs/assets/third-arm02.webp) | 
|:--:| 
| *Fasza harmadik kéz* |

Ez tűnik talán a leghasználhatóbbnak. Asztal szélére lehet erősen fogatni, tutira nem dől el. A nagyítója LEDes. Oda világít, ahova nézel vele. A négy kar lehet túlzásnak tűnik, mert legtöbbször kettő is elég, de a harmadikra szoktam az ón kerekét tenni forrasztás közben, így könnyen tekeredik le. A negyedik kart meg egyszerűen leszereled. :)
Másik alternatíva:  
[Dögös harmadik kéz](https://s.click.aliexpress.com/e/_A7AiVk)

| ![Dögös harmadik kéz](/docs/assets/third-arm03.webp) | 
|:--:| 
| *Dögös harmadik kéz* |

Ennek nem kis béna talpa van. Jó masszívnak tűnik, mert nagy a felülete, és fémből van. Ami tetszik benne, hogy van rövidebb, és hosszabb fogója is, illetve alul van 4 mágneses oszlopka, ami egy satut is tud helyettesíteni. Tudom, ezek drágák, nem is kötelező megvenni egyiket sem, főleg ha van már satud.


### Nagyító
Fontos, hogy legyen egy nagyítónk. Sokszor mesterséges fénynél forrasztva a flux, és az ón hasonlóan csillog, így könnyen lehet tévedni. Azt hisszük szépen összeforrasztottunk két szemet, közben csak a flux folyt oda, és nincs kapcsolat. Ezért kell a nagyító, hogy átvizsgáld vele amit csináltál.
Akinek jó a szeme, annak nem kell csak egy bármilyen kézi, például egy ilyen:  
[Kézi nagyító](https://s.click.aliexpress.com/e/_AXqkvy)

| ![Kézi nagyító](/docs/assets/magnifier01.webp) | 
|:--:| 
| *Kézi nagyító* |

Akinek nem, annak jobb egy rögzített példány, mert munka közben is lehet használni. Például ez:  
[Rögzített nagyító](https://s.click.aliexpress.com/e/_9RG8sK)

| ![Rögzített nagyító](/docs/assets/magnifier02.webp) | 
|:--:| 
| *Rögzített nagyító* |

### Gondolatok
Na hát nagyjából ennyit a forrasztási tapasztalataimról. Én ezeket használom. Lehet ismét más embereknek más vált/válik majd be, én ismét csak a saját kútfőmből beszélek. Ami nagyon fontos. Nem olyan veszélyes dolog ám a forrasztás. Rá kell érezni. Az SMD alkatrészekhez kell egy lapos fej, az fontos. De rakok be két videót, az egyik a forrasztásról szól, a másik a páka tisztításáról. Ami a lényeg, hogy ne félj tőle, gyakorolj, lehetőleg olcsó vackokon, és hidd el menni fog.
Ha bármi kérdésed lenne, kérdezd meg itt kommentben, vagy a Hobbielektronika facebook csoportban.
Továbbra is ajánlom a Hobbielektronika csoportot, a legjobb arcok, és a legsegítőkészebb szak, és barbár emberek gyűjtőhelyét! Mert kérdezni sose szégyen!


### Videók 
Köszönet és kudó Walter Reéb, Szabó Bálint illetve Professzore kollégáknak innen is! Nézzétek meg a többi videóikat is, én is nagyon sokat tanultam belőlük!


[SMD és DIP különbségek](https://youtu.be/XTjp5XcysEA)  
[Forrasztás alapok](https://youtu.be/XTjp5XcysEA)  
[SMD forrasztás alapok](https://youtu.be/jPYt-QsSz6M)  
[Páka hegy tisztítás és karbantartás](https://youtu.be/vZD5i4cWqoU)  
[TS100-as páka bemutató](https://youtu.be/-BcO63KE9FQ)  