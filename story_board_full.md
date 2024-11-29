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
### 2.1 ROS 2
- basics
- nodes
#### 2.1.1 ROS 2 client libraries: rclpy
https://docs.ros.org/en/foxy/Concepts/About-ROS-2-Client-Libraries.html#the-rclpy-package
#### 2.1.2 Interfészek (msg, srv)
https://docs.ros.org/en/foxy/Concepts/About-ROS-Interfaces.html
- msg - pub-sub
- srv - request-response
- action - goal-feedback-result
#### 2.1.3 Paraméterek
https://docs.ros.org/en/foxy/Concepts/About-ROS-2-Parameters.html
- parameter server
- node level
- launch level
- yaml level
- manipulating at runtime
#### 2.1.1 Executors
https://docs.ros.org/en/foxy/Concepts/About-Executors.html
- node handling - threads
- callback groups
### 2.2 Gazebo
https://gazebosim.org/features
- robot and world models
  - ode: http://ode.org/ode-latest-userguide.html
- sensors and noise models
- plugins - interaction trough topics
### 2.3 Nav2
- core concepts https://docs.nav2.org/concepts/index.html
- frames: https://www.ros.org/reps/rep-0105.html
- costmap representation
- odometry
#### 2.3.1 Planners
#### 2.3.2 Controllers
#### 2.3.3 Costmaps
#### 2.3.4 Navigator API
### 2.4 Lokalizáció - AMCL
https://docs.nav2.org/configuration/packages/configuring-amcl.html
### 2.2 Robotmodellek és szabályzók
#### 2.2.1 Differenciálhajtású robotok
### 2.3 Model Predictive Control (MPC)
### 2.4 MPPI szabályzó
- leírás
- képletek
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
