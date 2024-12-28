## 2. fejezet: Irodalmi áttekintés
- Alapfogalmak és definíciók.
- Főbb előnyök/hátrányok.
- Alkalmazási példák.
- Források (tudományos cikkek, ros2, nav2 dokumentációk)
- Ábrák és diagrammok (táblázatok)

### 2.1 Robotok mechanikai felépítése
Robotok mechanikai felépítésük alapján kétféle csoportra oszthatók: térbeli mozgásra képes és mozgásra nem képes alappal rendelkezők. A fix alaphoz kötött robotok geometriai felépítése leírható merev testek (links) és csuklók (joints) kapcsolatainak sorával, melyek egy adott munkatérben képesek mozogni. A mozgó alappal rendelkező robotok a térben helyet tudnak változtatni. Mechanikai szempontból egy vagy több merev testből állhatnak, melyekhez csatlakozik egy elmozdulásra képes rendszer például kerekek.
https://link.springer.com/book/10.1007/978-1-84628-642-1

### 2.2 Mobil alappal rendelkező robotok
Mobil robotok tovább csoportosíthatóak kerekekkel (vagy valamilyen elforduló mechaniozmussal) vagy lábakkal mozgó osztályokra. Továbbiakban a kerekekkel rendelkező robotokról lesz szó.

TODO: képek
Különféle kerék mechanizmusok definiálhatóak:
Fix kerekek, cska irányban forognak (előre-hátra), nem képesek elfordulni oldalirányban. Általában meghajtott kerekek tertoznak ide, amelyek a robot hajtását biztosítják, példál egy autó hátsó tengelyére szerelt kerekek. A robot bázisához mereven csatlakoznak és saját tengelyük körül forognak, amely ortogonális a kerék síkjára.
Irányítható (kormányozható) kerekek oldalirányban elfordíthatóak, a haladási irányuk megváltoztatható, például autó első tengelyén lévő kerekek. A robot bázisához egy csuklóval csatlakoznak, mely lehetővé teszi a kerekek elfordulását, illetve erre merőleges saját tengellyel rendelkeznek (szintén merőleges a kerék síkjára), melyek körül forognak.
Szabadonfutó (bolygó/caster) kerekek hasonló mechanikai csatlakozással rendelkeznek, mint az irányítható kerekek, azonban a robot bázisához való csatlakozásuknál található tengely körül szabadon fordulnak el, például irodai székek vagy bevásárló kocsi kerekei. A vertikális tengely nem metszi a kerék elfordulási tengelyét hanem egy "offset" távolságra helyezkedik el. Ezek a kerekek mechanikai stabilitásban segítik a robot bázist.
https://link.springer.com/book/10.1007/978-1-84628-642-1

### 2.3 Mobil kerekes robotok kinematikai modellje
TODO: képek és hivatkozások
Itt kétféle csoportosítás különíthető el: holonomikus (nem tud mozogni a sík bármelyik irányában) és omnidirekcionális (tetszőleges irányba képes mozogni). Omnidirekcionális robotok mecanum (másik nevén svéd) kerekekkel felszerelt robotok, melyek több forgó alkatrésszel rendelkeznek, a kerék kerületen mentén független elfordulni képes görgők vannak amik segítségével oldalazó mozgást is végezhet a kerék tengelyével párhuzamosan. A dolgozatben vizsgált robotmodellek holonomikusak. Több fajta (előző pontban tárgyalt) kerék elrendezéssel hozható létre ilyen robotmodell. Klasszikusan a tricikli modell, amely egy tengelyen két együtesen meghajtott kerékkel rendelkezik és egy kormányzott kerékkel. Az autókhoz hasonló modellek négy kerékkel ahol ebből kettő meghajtott és kettő kormányozható, vagy kettő egyszerre kormányozható és meghajtott plusz kettő stabilitásban aszisztáló fix kerékkel. Differenciál hajtású mobil robotok is a holonomikus robotok közé tartoznak, melyek két függetlenül meghajtott kerékkel és egy vagy több szabadon elforduló kerékkel szerelnek fel.
https://control.ros.org/rolling/doc/ros2_controllers/doc/mobile_robot_kinematics.html#omnidirectional-wheeled-mobile-robots
http://www.robotplatform.com/knowledge/Classification_of_Robots/Holonomic_and_Non-Holonomic_drive.html


### 2.4 Differenciál hajtású robotok
TODO: képletek (egyenletek és pozíció vektor), ábra
A diplomamunka során használt robotok közül mindegyik ebbe a kategóriába esik. Két szeparáltan meghajtott kerekének köszönhetően egyhelyeben képes megfordulni. A forgás tengelye a két kerék tengelyének közzéppontja. A passzív caster kerék vagy kerekek a stabilitásban segítenek, ezek lekövetik a robot mozgását. Ugye egy sík három pontból már felírható ezért a robot statikai egyensúlya nem jelent problémát, amíg a tömegközéppont vetülete a három vagy több kerek talajal való találkozási pontjainak egyenes szakaszokkal összekötő polinom belsejében marad. Mint mobil robot a differenciel hajtású szerkezzetek munkatere virtuálisan végtelen, ha a munkateret a környezet egy altereként értelmezzük. A valóságban természetesen előjönnek olyan korlátok, mint a robot fizikai kiterjedése és a környezetben lévő akadályok relatív mérete és pozíciója. Természetesen itt sík felületet feltételezve (és kizárva lépcsőket, lifteket stb.) Mint nem omnidirekcionális robotmodell a lokális elmozdulására esnek korlátok. Nem tud rögtön a hajtott kerekek tengelyére merőleges irányába elmozdulni, ehhez szükséges fordulnia. De képesnek tekinthető bármely pozíciót felvenni csak nem rögtön. Ez úgy is kifejezhető, hogy a robot szabadsági fokainak száma alacsonyabb, mint a pozíciót leíró vektor változói.

- mozgásegyenletek
- előnyök, hátrányok más robotmechanizmusokkal szemben
- turtlebot példa
https://control.ros.org/rolling/doc/ros2_controllers/doc/mobile_robot_kinematics.html#omnidirectional-wheeled-mobile-robots
https://link.springer.com/book/10.1007/978-1-84628-642-1
https://link.springer.com/chapter/10.1007/978-1-84628-642-1_8

https://hades.mech.northwestern.edu/index.php/Modern_Robotics


### 2.3 Irányítások áttekintése a robotnavigációban

page: 517

- PID, Carrot, DWB, (MPC, MPPI későbiekben részletesen)
- előnyök, hátrányok
### 2.4 Model prediktív szabályozás
- előnyei (előrejelzés, optimalizálás)
- hátrányai (számításigény)
### 2.5 MPPI szabályzó
- alapelvek: Monte Carlo szimuláció, költségminimalizálás
- kihívás: számításigény, finomhangolás komplexitása
- alkalmazási példa
#### 2.5.2 Eltérések MPC-től
#### 2.5.2 Megvalósítás NAV 2-ben