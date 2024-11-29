## 2. fejezet: Irodalmi áttekintés
- Alapfogalmak és definíciók.
- Főbb előnyök/hátrányok.
- Alkalmazási példák.
- Források (tudományos cikkek, ros2, nav2 dokumentációk)
- Ábrák és diagrammok (táblázatok)
### 2.1 Robotmodellek
- kinematikai és dinamikai modellek
- differenciálhajtású, holonom, omniwheel
https://control.ros.org/rolling/doc/ros2_controllers/doc/mobile_robot_kinematics.html#omnidirectional-wheeled-mobile-robots
https://link.springer.com/chapter/10.1007/978-1-84628-642-1_8
https://hades.mech.northwestern.edu/index.php/Modern_Robotics

Többféle robot modell létezik.
- csoportosítást megengmlíteni
- lekerekíteni hogy itt kerékkel rendelkező robotokról van szó melyek képesek autonóm navigálni
- modellek leírása kinamatika egyenletekkel
- holonomic v non-holonomic robotok
- felsorolni a holonomic: annyi felé tud haladni ehány szabadsági foka van pl omni wheel
- http://www.robotplatform.com/knowledge/Classification_of_Robots/Holonomic_and_Non-Holonomic_drive.html
- non holonomic: nem tud annyi felé menni mint ahány szabadsági foka van pl autó
- átkerekítani hogy többiekben a differenciál hajtású robotokról lesz szó

### 2.2 Differenciálhajtású robotok
- mozgásegyenletek
- előnyök, hátrányok más robotmechanizmusokkal szemben
### 2.3 Szabályzók áttekintése a robotnavigációban
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