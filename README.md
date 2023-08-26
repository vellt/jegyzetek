# Git verziókezelés

A Git egy parancssori eszköz, bár manapság minden IDE támogatja beépített GUI modul formályában. A verzió kezelés lelke. Egy valamire való fejlesztő enélkül ki se lép az ajtón. 

Célja, hogyha eleinte csak Lokálisan gondolkozunk és mondjuk a szomszéd poénból 20 percig folyamatosan töröl meg módosít a projektünkben, vissza tudjunk állni bármelyik korábbi működő verzióra. 

Megosztott munkavégzésre is kitünő, hiszen visszatekinthető, hogy ki, mit és hol módosított. Ez biztosít számunkra egy olyan rendszert, amely felügyeli a projektváltozását annak életciklusa során (hogyan, mikor, kiáltal, miért). Időtöl és tértől függetlenül akármennyien dolgozhatnak egy projekten. 

![](https://github.com/vellt/readme/blob/git_kezeles/git.jpg?raw=true)

## Kulcsszavak

- Local (add, commit)

- Remotes (clone, push, pull)

- commit workflow (add, commit, push)

- commit version history: A verziók láncként egymásra épülnek. ".git" rejtett foleren belül érhető el. Kitörölni szigorúan TILOS. A projekt verziókezelését felügyeli. Lehetővé teszi, hogy akármelyik pillanatban vissza tudjunk állni egy régebbi állapotra.

- Branch, checkout

- merge, merge conflicts

## Alapvető parancssori utasítások

Kedvenc terminálunk a Windows PowerShell, ami egy szteroidozott CMD. Mivel a Git egy parancssori eszköz így pár alapvető parancssori utasítással is meg kell ismerkedni. Ha valamilyen parancs után pontot teszünk, az az aktuális mappát hivatkozza le.

### PowerShell utasítások

```yaml
dir            # látható könyvtár tartalom
ls             # látható könyvtár tartalom
ls -hidden     # rejtett könyvtár tartalom
ls -force      # rejtett + látható könyvtár tartalom
get-childitem -hidden     # rejtett + látható állományok
get-childitem -force      # rejtett + látható könyvtár tartalom
new-item test.txt         # készít egy test.txt üres állományt
mkdir          # mappa készítése
cd             # ugrálás a mappák között
cd..           # vissza lépés egy mappával
cls            # törli a képernyőt, ha már tele spammeltük
cmd            # betölti a cmd terminált
exit           # általában arra kell hogy bezárjuk a megnyitott cmd-t
start          # elindít bármit, amihez van alapértelmezés (sln, txt, md)
explorer .     # az aktuális foldert megnyitja a fájlkezelőben
code .         # az akt. foldert megnyitja a Visual Studio Code-ban    
ctrl +c        # (billentyűzet kombináció) folyamat megszakító
```

### CMD utasítások

Ha egy-két utasítást nem tudunk lefuttatni PowerShell-ben, vagy csak szeretnénk egy két CMD specifikus parancsot lefuttatni, át kell lépni a CMD-be, a  **cmd** PowerShell parancsal, elvégezzük amiket szeretnénk, majd **exit**-el visszalépünk a PowerShell-be.

```yaml
dir /a                 # rejtett + látható könyvtár tartalom
copy nul > test.txt    # tetszőleges állomány készítése
copy con test.txt      # tetszőleges állomány készítése
```

### Git utasítások

```yaml
git init .             # df
git status
git add <file>
git add --all
git add test/
git add .
git commit -m "leírás"
git config -l            # lokálisnál lehet hasznos
git config --global user.email ".."
git config --global user.name ".."
git log
git reset --hard HEAD ~1
```

![](https://github.com/vellt/jegyzetek/blob/git_kezeles/github_diagram.drawio.png?raw=true)



Git 2. kép



4 fő állapota egy fájlnak

Untracked - nem figyelt

Unmodified - nem módosított

Modified - módosított

Staged - előkészült mentésre



A git mikor egy Untracked fájlt megfigyelés alá vesz, akkor átkerül a Staged állapotba, itt a fájlok elő vannak készítve a mentésre. Azok a fájlok amik a következő mentésbe benne lesznek az a stage-be lesznek. H egy staged részen lévő fájlt módosítani szeretnénk és ezt a változást rögzíteni is akarjuk, akkor commit-ot fogunk csinálni, ekkor  a fájl állapota átkerül, stagedből unmondified-ra. Most már a fájl olyan mintha nem is módosítottuk volna, ha ezt megint módosítanánk, átkerül az Unmondofed-be, es ha azt akarjuk h az az állapot bekerüljön a mentésbe, át kell tenni onnan a staged állapotba. A fájlunk ebben a 3 állapotban forog, míg úgy nem döntünk hogy kivesszük a gitkezelésből, ekkor visszakerül az Untracked állapotba
