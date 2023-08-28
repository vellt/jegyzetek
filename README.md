# Git verziókezelés

A Git egy parancssori eszköz, bár manapság minden IDE támogatja beépített GUI modul formályában. A verzió kezelés lelke. Egy valamire való fejlesztő enélkül ki se lép az ajtón. 

Célja, hogyha eleinte csak Lokálisan gondolkozunk és mondjuk a szomszéd poénból 20 percig folyamatosan töröl meg módosít a projektünkben, vissza tudjunk állni bármelyik korábbi működő verzióra (commit-ra). 

Megosztott munkavégzésre is kitünő, hiszen visszatekinthető, hogy ki, mit és hol módosított. Ez biztosít számunkra egy olyan rendszert, amely felügyeli a projektváltozását annak életciklusa során (hogyan, mikor, kiáltal, miért). Időtöl és tértől függetlenül akármennyien dolgozhatnak egy projekten. 

![](https://github.com/vellt/readme/blob/git_kezeles/git.jpg?raw=true)

## Pár fontosabb Git kifejezések

- Local (add, commit)

- Remotes (clone, push, pull)

- commit workflow (add, commit, push)

- commit version history: A verziók láncként egymásra épülnek. ".git" rejtett foleren belül érhető el. Kitörölni szigorúan TILOS. A projekt verziókezelését felügyeli. Lehetővé teszi, hogy akármelyik pillanatban vissza tudjunk állni egy régebbi állapotra.

- Branch, checkout

- merge, merge conflicts

- HEAD: a legutolsó commit)

- gitignore

## Alapvető parancssori utasítások

Kedvenc terminálunk a Windows PowerShell, ami egy bővített utasításkészletű CMD. Mivel a Git egy parancssori eszköz így pár alapvető parancssori utasítással is meg kell ismerkedni. 

### PowerShell utasítások

(Ha valamilyen parancs után egy pontot teszünk, az az aktuális mappát hivatkozza le.)

```yaml
dir / ls           # az aktuális könyvtár minden látható elemét kilistázza
ls -hidden / -h    # az aktuális könyvtár minden rejtett elemét kilistázza
ls -force / -fo    # az aktuális könyvtár minden rejtett + látható elemét kilistázza
get-childitem -hidden / -h     # rejtett + látható állományok
get-childitem -force / -fo     # rejtett + látható könyvtár tartalom
new-item <file>                # készít egy tetszőleges állományt pl egy test.txt-t    
remove-item <file>             # törli a kijelölt elemet az aktuális könyvtárból
rename-item / ren <old> <new>  # fájlok/mappák átnevezése
mkdir <folder>     # mappa készítése
rmdir <folder>     # mappa törlése
cd <path>          # a paraméterként megadott könyvtárra való átlépés
cd..               # vissza lépés egy mappával
cls                # törli a képernyőt, ha már mondjuk tele spammeltük
cmd                # betölti a cmd terminált, amit az exit paranccsal zárjuk le.
start              # elindít bármit, amihez van alapértelmezés (sln, txt, md)
explorer .         # az aktuális foldert megnyitja a fájlkezelőben
code .             # az akt. foldert megnyitja a Visual Studio Code-ban    
ctrl +c            # (billentyűzet kombináció) folyamat megszakító
```

###### Git utasítások

```yaml
git init .                # létrehozza a kező git állományokat
git status                # megmutatja, hogy milyen változásokat hoztál létre vagy módosítottál a projektedben, és azt is, hogy ezeket még nem vagy készen elküldeni a Git követésére.
git add <file>            # a munkamappbán belül található konkrét állomány hozzáadása a staging area-hoz
git add --all             # a teljes munkamappában lévő minden változtatást hozzáadja a staging area-hoz, beleértve a törölt fájlokat és a .gitignore-ban meghatározottakat is. 
git add test/             # a munkamappbán belül található test mappában végzett változtatásokat hozzáadja a Git követési listájához (staging area)
git add .                 # a munkamappban módosított és újonnan létrehozott fájlokat hozzáadja a Git követési listájához (staging area)
git commit -m "leírás"    # parancs segítségével létrehozol egy új "commitot" a Git verziókezelő rendszerben. Egy commit egy pillanatkép a projekt állapotáról, amely tartalmazza a módosított vagy újonnan létrehozott fájlokat és azok tartalmát.
git config -l             # Git beállításainak listázására szolgál (lokálisnál gitkezeléskor lehet hasznos nekünk)
git config --global user.email ".."  # segítségével beállíthatod a globális felhasználó e-mail címét a Git konfigurációdban. 
git config --global user.name ".."   # parancs segítségével beállíthatod a globális felhasználó nevét a Git konfigurációdban. 
git log                   # segít megjeleníteni a projekt előzményeit vagy más szóval "commit" történetét.
git reset --hard HEAD ~1  # segít visszatérni az előző commit állapotába és eldobni az utolsó commitot. --hard kapcsoló: A változtatásokat a munkamappában és a staging area-ban is eldobod. HEAD~1: azt jelenti, hogy az utolsó commit előtti commitra kívánsz visszalépni. Ha az utolsó mentett commiitra szeretnék vissza állni: git reset --hard HEAD
```

![](https://github.com/vellt/jegyzetek/blob/git_kezeles/github_diagram.drawio.png?raw=true)



## 4 fő állapota egy fájlnak

- Untracked - nem figyelt

- Unmodified - nem módosított

- Modified - módosított

- Staged - előkészült mentésre

![](https://raw.githubusercontent.com/vellt/jegyzetek/git_kezeles/git2.png)

###### Git Statement workflow

Mikor a **Git** egy *Untracked* fájlt megfigyelés alá vesz, akkor átkerül a *Staged* állapotba, itt a fájlok elő vannak készítve a mentésre. Azok a fájlok amik a következő mentésbe benne lesznek az a *staged*-be lesznek. Ha egy, a *staged* állapotban lévő fájlt módosítunk és ezt a változást rögzíteni is akarjuk, akkor egy új *commit*-ot kell készíteni róla, ekkor a fájl állapota átkerül a *staged*-ből *unmodified*-be. Most már a fájl logikailag olyan mintha nem is módosítottuk volna, ha ezt megint módosítjuk,



 átkerül az *Unmondifed*-be, és ha azt akarjuk h az az állapot bekerüljön a következ mentésbe, át kell tenni onnan a staged állapotba. 



A fájlunk ebben a 3 állapotban forog, míg úgy nem döntünk hogy kivesszük a gitkezelésből, ekkor visszakerül az Untracked állapotba
