# TW5-github-actions

- inspirálta
  - https://github.com/saqimtiaz/TW5-github-actions-example/tree/main
  - 


## Saq

Példa a Github Actions használatára egy TiddlyWiki létrehozására és közzétételére

A konfigurálás után minden alkalommal, amikor módosításokat hajt végre a tárhelyen, egy frissített TiddlyWiki fájl készül, és egy nyilvános URL-címen közzéteszi.

Kiindulópont: egy wiki mappa a node.js-es TiddlyWiki számára, amelyet egy Github tárhelybe mentünk.

A tárhely gyökerében a következőket kell tennie:

- `package.json` fájl hozzáadása. 
  - Ezt megteheti az `npm`-en keresztül az `npm init` használatával, 
  - vagy az ebben a tárban lévő `package.json` fájl másolásával és módosításával.
- add hozzá a TiddlyWikit függőségként `npm install tiddlywiki`
- Adjon hozzá egy szkriptet a `package.json` fájlhoz úgy, hogy kimásolja a `package.json` fájlt ebben a tárhelyben, és módosítsa úgy, hogy az megfeleljen a lerakat gyökérében futtatandó parancsnak a TiddlyWiki létrehozásához. Ha a `tiddlywiki.info` fájl a lerakat gyökérkönyvtárában található, akkor ezt nem kell módosítania.
  - Az `npm run build` paranccsal ellenőrizheti, hogy eddig minden működik, a wiki HTML fájlt a tárhely gyökérkönyvtárának `output` könyvtárában kell elmenteni. Ez a könyvtár a tesztelés után biztonságosan törölhető.


