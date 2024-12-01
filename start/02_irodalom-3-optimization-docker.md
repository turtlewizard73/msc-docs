https://web.stanford.edu/group/sisl/k12/optimization/MO-unit1-pdfs/1.1optimization.pdf
from page 8
### 2.5 Optimalizációs eljárások
1. **Mi az optimalizáció?**
   - Matematikai értelemben: célfüggvény minimalizálása/maximalizálása.
   - Gyakorlati értelemben: adott korlátozó feltételek mellett a legjobb megoldás megtalálása.

2. **Optimalizációs alapfogalmak**
   - **Célfüggvény**: az a függvény, amelynek értékét optimalizálni szeretnénk.
   - **Keresési tér**: a lehetséges megoldások halmaza.
   - **Globális vs. lokális optimum**: a keresési tér különböző pontjainak értékelése.
   - **Exploráció és exploitáció**: új területek felfedezése és az ismert jó területek finomítása.

3. **Optimalizációs problémák osztályozása**
   - **Lineáris vs. nemlineáris problémák**.
   - **Korlátos és korlátlan optimalizáció**.
   - **Folytonos és diszkrét keresési tér**.

4. **Az MPPI probléma mint optimalizációs feladat**
   - Az MPPI (Model Predictive Path Integral) célfüggvénye és keresési tere.
   - Az optimalizáció kihívásai: nemlineáris pályatervezés, dinamikus akadályok kezelése.
   - Miért fontos az optimalizáció az MPPI teljesítményének javításához?

5. **Az optimalizáció kihívásai és szempontjai**
   - **Számítási komplexitás**: iterációk száma, mintavételezés hatékonysága.
   - **Pontosság és konvergencia**: hogyan garantáljuk, hogy a legjobb megoldáshoz jutunk?
   - **Robustság**: hogyan kezeljük a zajos vagy bizonytalan bemeneteket?

6. **Optimalizációs algoritmusok szerepe a gyakorlatban**
   - Példák: mesterséges intelligencia, robotika, pénzügyi modellezés.
   - Az egyes algoritmusok előnyei és hátrányai.

7. **Hogyan válasszunk algoritmust?**
   - Problémaspecifikus tényezők: keresési tér típusa, számítási erőforrások korlátozottsága.
   - Az MPPI-hez illeszkedő algoritmusok áttekintése.

#### 2.5.1 Random search
#### 2.5.2 Grid search
#### 2.5.3 Bayesian optimization


### 2.6 Docker
A Docker egy konténerizációs platform, amely lehetővé teszi alkalmazások és azok összes függőségének elkülönített környezetben történő futtatását. A konténerek számíti igényt tekintve alcsonyabb, önálló, végrehajtható egységek, amelyek tartalmazzák a futtatáshoz szükséges összes erőforrást, például könyvtárakat, csomagokat és konfigurációkat. Ez jelentősen különbözik a hagyományos virtuális gépektől, amelyek külön operációs rendszert is igényelnek, így nehezebbek és erőforrás-igényesebbek. Ezek mellett az alap operációs rendszer fájljaihoz, hardvereihez is bonyolultabb hozzáférésre van csak lehetőség virtuális gépek használata során. A Docker segítségével egy fejlesztési környezet gyorsan beállítható, migrálható és párhuzamosítható, ami ideális a ROS 2 alapú alkalmazások fejlesztéséhez.

A Docker használata számos előnyt nyújt a fejlesztés során. Az egyik legfontosabb előny, hogy elkülönített környezetet biztosít. Ez azt jelenti, hogy a ROS és Python csomagok különállóan kezelhetők, elkerülve a függőségek ütközését vagy verziók közötti inkompatibilitásokat. Így különböző projektek párhuzamos fejlesztése esetén sem kell aggódni a környezetek összekeveredése miatt. Emellett a konténerek könnyen újraalkothatók és megoszthatók, így a fejlesztőcsapat minden tagja ugyanabban a pontosan definiált környezetben dolgozhat. A csomagok, szoftverek az alap operációs rendszertől elkülönítve telepíthetők egy konténerben, ezért a fejlesztő terhét könnyíti.

A Docker konténerek garantálják, hogy minden fejlesztési környezet teljesen izolált legyen. Ez különösen fontos a ROS ökoszisztémában, ahol számos különféle csomag és függőség együttműködése szükséges. A Python csomagok és ROS könyvtárak kompatibilitása kritikus a sikeres fejlesztéshez. Egy jól definiált Docker image segítségével biztosítható, hogy a szükséges csomagok és verziók mindig elérhetők és a megfelelő konfigurációval futnak.

A konténerizáció további előnye, hogy könnyen lehetővé teszi több környezet párhuzamos futtatását ugyanazon a rendszeren. Például, ha a Gazebo szimulátort több különböző projekthez szeretnénk használni, a konténereknek köszönhetően külön portokat állíthatunk be, így elkerülve az ütközéseket. Hasonlóképpen, a ROS rendszerben a ROS_DOMAIN_ID segítségével konténerek között elkülöníthetők a kommunikációs csatornák. Ez lehetővé teszi, hogy több robot vagy szimuláció különállóan működjön ugyanazon a gépen, anélkül, hogy azok interferálnának egymással.
