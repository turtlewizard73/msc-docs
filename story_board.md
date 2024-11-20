# DIPLOMAMUNKA
## Feladatok:
1. Készítsen irodalmi áttekintést a MPPI szabályzókról és hangolási módszerekről!
2. Dolgozzon ki egy szimulációs eszközt a MPPI szabályzó hangolásához ROS2 környezetben!
3. Implementáljon egy optimalizációs eljárást a MPPI szabályzó paramétereinek automatikus
hangolására!
4. Végezzen méréseket és értékelje a különböző hangolási módszerek hatékonyságát és pontosságát!
5. Készítsen összefoglalót a munkájáról!

# Tartalom
## 1. fejezet Bevezetés
 - általánosan probléma körbejárása
   - felvázolva a A->B-be eljutás problémáját
   - robot rendszer összetettség, komplexitás
   - komponensek feladatkörök leírása
     - planner
     - controller
 - specifikusan céges példa problémára
   - hangolás nem egyértelmű, kevés leírás
   - nagy tér, plan újratervezés compute költséges
 - hogyan lehet megoldani a problémát ...
   - célok:
     - jobb paramétereket találni default robotra
     - jobb paramétereket találni specifikus robotra
       - behelyettesíthető legyen adott robot modell
     - másra lehet e használni az mppi controller
 - szimulációs környezet szükségessége
 - optimalizációs eljárások
 - mérések és kiértékelés
   - miket kellene mérni?
   - miért azokat?
   - MÉRÉS megismételhetősége

## 2. fejezet Irodalmi áttekintés
Részletesen minden technológiáról?
- differenciálhajtású robotok és szabályzók
- ros2 - lehet copypasta bsc-ből?
  - gazebo szimulációs környezet és problémái
  - környezet - launch fileok stb
- nav2
  - struktúra
  - lokalizáció - navigáció kérdés
  - szabályzók
  - navigator API
- mppi
  - modelprediktív szabályzók
  - mppi általánosságban
  - mppi nav2-es megvalósítás
- docker
  - csupa jóság
  - ros2-es konténer
  - így duplikálható -> szimulációk párhuzamosíthatók
- optimalizációs eljárások (lehet többről is írni mint megvalósított?)
  - random search
  - grid search
  - genetic algorithms - csak az öreg Botzheim emlékére akár meg is lehetne csinálni
  - bayesian optimization
- mérések és kiértékelések
  - gyűjtött adatok miért ezeket? (lehet kövi fejezet)
- python csomagok
  - ha nem lenne elég az 50 oldalhoz chatgpt megtolhatja
  - scikit talán a bayesian opt-hoz

## 3. fejezet Szimulációs eszköz tervezése és megvalósítása
főleg ROADMAP-ek tartalma
irodalmi áttekintésben ros2 nav2 gazebo alapok itt az actual problémák és megoldásuk, végtelen oldal úgyse olvassák el
- dev container
  - docker image
  - ezen belül ros2
- nav2 fork
  -


## 4. fejezet Optimalizációs eljárások - megvalósítás
ez a fejezet annyira nem hosszú, lehetne meg egy kettő optimalizációs eljárást lekódolni és mondjuk összehasonlítani egy este alatt mennyire jut (biztos lesz rá idő)
- optmalizálás
  - input, output
  - score fgv (itt is össze lehetne hasonlítani többet)
   - casual (távolság szögben, frechet, footprint cost, elapsed time)
   - dinamikai (rms)
   -
Itt amúgy mindegyikről lehet írni mennyi idő, vagy erőforrásokról (compute)
- vagy átrakni ide az irodalomkutatásos részt
- random search
  - meghatározott min-max-ig felbontással
  - uniform
- gridsearch
  - függetlenek vagy függnek e a paraméterek ki lehet tárgyalni
- bayesian optimization
  - scikit learn
  - miért jobb mint a többi

## 5. fejezet Mérések és kiértékelés
- elvégzett mérések kiértékelése
- adatok grafikonok

## 6. fejezet Összefoglalás



# TODO: mérések
1. Kérdés: tudunk e kitalálni jobb paramétereket mint a default?
  - metrikák 1 (fő feladat érdekel):
    - elapsed time -> érjen oda időben
    - avg footprint cost -> ne menjen át akadályon (lehető legszabadabb területen menjen át)
    - distance from goal -> érje el a célt
    - angle from goal -> érje el a célt
    - frechet distance -> mennyire követi az útvonalat (AMI UGYE SZEREPE)
  - metrikák 2 (mellékesen hogy el lehet e érni):
    - rms acceleration -> ne legyen rángatózás
    - rms jerk -> ne legyen rángatózás
    - frechet nem számít (mert nem érdekel az útvonal)
    - elapsed time kisebb súly
    - metrik1-ek kisebb súllyal

2. jobb paramétereket találni specifikus robotra
  - metrikák 1 & metrikák 2 alapján külön külön

3. másra lehet e használni az mppi controller? -> akadály kikerülés replan nélkül
  - metrikák 1 alapján főleg


| # | Mérés | Robot | Paraméterek | Mi esik ki belőle? |
|-|-|-|-|-|
| 1 | baseline | waffle | nav2 default x 100 | alap paraméterekkel milyen a szórása |
| 1.a | grid | waffle | nav2 default x kritik * 100 | milyen hatással vannak a kritikek -> jó sokféle plot|
| 1.b | random | waffle | random x SOK | mennyire találja el a legjobbat |
| 1.c | bayesian | waffle | durranjon | (hihihaha az előzőek eredményeit már lehet használni a paramétertérhez szóval lehet kevesebb szimut kell nyomni) |
| 2 | baseline | burger | nav2 default x 100 | szórása |
| 2 | baseline | enjoy | nav2 default x 100 | szórása - mennyi a diff az eredetitől |
| 2.a | grid | enjoy | ... | ... |
| 2.b | random | enjoy | ... | ... |
| 2.c | bayesian | enjoy | ... | ... |
| 3 | bayesian | waffle | nav2 default x növekvő akadály | mindegyikre n try, ha átjut rajta n-2-szer szupi, ha nem akkor tovább iterálni arról a pontról |

