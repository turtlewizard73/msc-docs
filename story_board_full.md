# DIPLOMAMUNKA
**Cím:**
*MPPI szabályzó optimalizálása szimulációs környezetben ROS2 platformon*

---

## Feladatok
1. Készítsen irodalmi áttekintést a MPPI szabályzókról és hangolási módszerekről!
2. Dolgozzon ki egy szimulációs eszközt a MPPI szabályzó hangolásához ROS2 környezetben!
3. Implementáljon egy optimalizációs eljárást a MPPI szabályzó paramétereinek automatikus hangolására!
4. Végezzen méréseket és értékelje a különböző hangolási módszerek hatékonyságát és pontosságát!
5. Készítsen összefoglalót a munkájáról!

---
KÉSZ: md
## 1. fejezet: Bevezetés
- pár mondatban miről fog szólni, mit csináltam
### 1.1 Autonóm navigáció kihívásai
- 2 mondat
#### 1.1.1 Általános probléma bemutatása
- A->B probléma
#### 1.1.2 Implementáció és keretrendszer problémája
- becsomagolva ros2 és nav2ben jó de rossz is
#### 1.1.3 Specifikus megoldások problémája
- mi van akkor ha el kell térni bizonyos funkciókhoz
#### 1.1.4 Időigényesség és szimuláció
- paramétert optimalizálni sok idő
#### 1.1.5 Navigációs rendszer
- általánosan a navigációról (planner, controller stb.)
### 1.2 Motiváció
### 1.3 Kihívások megoldása
### 1.4 A diplomamunka célkitűzései
#### 1.4.1 Eszköz fejlesztése a MPPI szabályzó hangolásához
- legyen mérhető, metricák alapján értékelhető
- izolált minél jobban fókuszálva paraméterekre
- egyszerű
- könnyen paraméterezhető
- megismételhető
#### 1.4.2 Jobb paraméterek meghatározása
- hangolási eszköz validitálása
- out of the box paraméterek validitálása
#### 1.4.3 Paraméterhangolás kidolgozása általános robotmodellre
#### 1.4.4 Optimalizációs eljárások alkalmazása és összehasonlítása

---

## 2. fejezet: Irodalmi áttekintés
(irodalom part1)
### 2.1 Robotok mechanikai felépítése
### 2.2 Mobil alappal rendelkező robotok
### 2.3 Mobil robotok kinematikai modellje
### 2.4 Differenciál hajtású robotok
TODO: képletek

TODO: fullosan, források megvannak
### 2.3 Irányítások áttekintése a robotnavigációban
### 2.4 Model prediktív szabályozás
### 2.5 MPPI szabályzó
#### 2.5.2 Eltérések MPC-től
#### 2.5.2 Megvalósítás NAV 2-ben

(irodalom part 2)
KÉSZ: md
### 2.1 ROS 2
#### 2.1.1 Modularitás és node-ok
#### 2.1.2 ROS 2 client library: rclpy
#### 2.1.3 Launch fájlok
#### 2.1.4 Interfészek
#### 2.1.5 Paraméterek
#### 2.1.6 Executors
#### 2.1.7 Composition
### 2.2 Gazebo
### 2.3 Nav2
#### 2.3.1 Costmap
#### 2.3.2 Planners
#### 2.3.3 Controller-ek
#### 2.3.4 Navigator API
### 2.4 MPPI Nav2-ben
#### 2.4.x MPPI Controller paraméterei
TODO: giga formázások
### 2.5 Odometria és TF
### 2.5 Lokalizáció - AMCL

(irodalom part 3)
### 2.5 Optimalizációs eljárások
#### 2.5.1 Random search
#### 2.5.2 Grid search
#### 2.5.3 Bayesian optimization

### 2.6 Docker
- miért hasznos
- elkülönített környezet - ros és python csomagok
- gazebo külön port
- ros domain id

---

## 3. fejezet: Szimulációs eszköz tervezése és megvalósítása
#### 3.1 Problémafelvetés
- bemenetek: 8 kritika/paraméter
- kimenet: döntési függvény (jobb, rosszabb)?
#### 3.2 Szimulációs környezet
- minimális számú nodeok
- launch file, legyen külön indítható egyszer
- legyen egy futtatható benchmark
- legyen egy optimizer (for loop benchmarknak)
- Robotmodellek integrálása (pl. TurtleBot).
- Akadályok és dinamikus környezet szimulálása.
#### 3.3 Mért adatok
#### 3.4 Kalkulált adatok
- inspiráció, kiindulás

---

## 4. fejezet: Optimalizációs eljárások megvalósítása
### 4.1 Optimalizációs folyamatok
- Input és output paraméterek definiálása.
- Értékelési függvények (score function) megtervezése:
  - Idő, költségek, útvonal-eltérés, akadályoktól való távolság.
### 4.2 Optimalizációs eljárások
### 4.2.1 Random search
- egyszerű implementáció, időigény.
### 4.2.2. Grid search
- paraméterfüggőségek vizsgálata.
### 4.2.3 Bayesian optimization
- könyvtárak és eredmények összehasonlítása.
### 4.3 Score függvények meghatározása

---

### 5. fejezet: Mérések és kiértékelés
#### 5.1 Adatgyűjtés
- Mért adatok:
  - Utazási idő, energiafogyasztás, akadályoktól való távolság, pontosság.
- Szimulációs eredmények dokumentálása.
#### 5.2 Eredmények grafikus kiértékelése
- Grafikonok és diagramok az egyes módszerek teljesítményéről.
- Megállapítások a paraméterhangolás hatékonyságáról.

---

### 6. fejezet: Összefoglalás és javaslatok

- A munka eredményeinek összegzése.
- Javaslatok további fejlesztésekre:
  - Valós robotokon történő validáció.
  - Új optimalizációs eljárások kipróbálása.

---

## Kiegészítendők és részletek

- MPPI matematikai modellje (whitepaper alapján).
- Az alkalmazott Python csomagok listája (pl. NumPy, SciPy, Scikit-learn).
- Ros2 paraméterek és kritikusok részletei (Nav2 API).
- Benchmark eredmények táblázatos és grafikus formában.


---


# Mobil robot irányítás

## 1. Bevezetés
- **Miért fontos a mobil robotok irányítása?**
  - Autonóm robotok szerepe különböző alkalmazásokban (logisztika, egészségügy, stb.).
  - A pontos és megbízható vezérlés jelentősége a robotok autonóm működésében.

## 2. Robotmodellek és vezérlésük
### 2.1 Kinematikai modellek
- A robotok mozgásának alapjai: kinematikai és dinamikai modellek.
- Példák különböző típusú mobil robotokra:
  - Differenciálhajtású robotok (pl. TurtleBot).
  - Holonom robotok (pl. omniwheel robotok).
  - Nonholonom robotok korlátai és vezérlésük kihívásai.

### 2.2 Vezérlési problémák
- Útvonal követése, akadályelkerülés, stabilitás biztosítása.
- Általános vezérlési módszerek mobil robotoknál.

## 3. Szabályzók mobil robotokhoz
### 3.1 Egyszerű szabályzók
- Proporcionális szabályozás (pl. "carrot chasing" módszer).
- Előnyei és korlátai.

### 3.2 Komplexebb szabályzók
- Dinamikai modelleken alapuló szabályozók.
- A PID szabályozás szerepe és alkalmazása mobil robotoknál.
- Gyakorlati kihívások, példák (pl. nemlineáris rendszerek kezelése).

## 4. Modell prediktív szabályozás (MPC)
### 4.1 Az MPC alapjai
- Hogyan működik az MPC?
- Költségfüggvény, korlátok és optimalizáció szerepe.
- Példák: ipari alkalmazások és robotvezérlés.

### 4.2 MPC mobil robotoknál
- Miért hasznos MPC mobil robotokhoz?
- MPC alkalmazása útvonaltervezésre és akadályelkerülésre.
- Példa algoritmus: a Linear Quadratic Regulator (LQR).

### 4.3 Kihívások MPC szabályzóknál
- Valós idejű számítási igények.
- Környezeti bizonytalanságok kezelése.

## 5. Modell prediktív pályaintegrálás (MPPI)
### 5.1 Az MPPI alapelvei
- Hogyan különbözik az MPPI az általános MPC-től?
- Az MPPI alapfogalmai: sztochasztikus mintavételezés, költségfüggvény minimalizálás.

### 5.2 MPPI mobil robotokhoz
- Az MPPI előnyei mobil robotok esetében: dinamikus akadályelkerülés, rugalmasság.
- A Nav2 MPPI implementáció bemutatása.

### 5.3 Példák és alkalmazások
- Esettanulmányok mobil robotoknál.
- Miért válik egyre népszerűbbé az MPPI a robotikában?

---

## Lehetséges mélységek a fejezetekben
- **Ábra és grafikon lehetőségek:**
  - Kinematikai modellek ábrái.
  - MPC és MPPI költségfüggvény összehasonlítása.
  - Valós és szimulált pályák eredményei.

- **Kód vagy pszeudokód bemutatása:**
  - MPC és MPPI alapalgoritmusok lépéseinek illusztrálása.
  - Egyszerű példák Pythonban.
