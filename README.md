# TW5-github-actions

- inspirálta
  - https://github.com/saqimtiaz/TW5-github-actions-example/tree/main


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
- Másolja a tárhely gyökérkönyvtárába a `.github` könyvtárat ebből a tárolóból.
- Adja hozzá ezeket az új fájlokat a Githez, véglegesítse és küldje el a Githuba.
- A TiddlyWiki automatikusan létrejön, és a `gh-pages` ágába kerül.
- Ha még nincs engedélyezve a Github Pages a tárhelyén, lépjen a tárhely settings oldalára, és válassza a bal oldali menü Pages menüpontját. A 'Source' alatt válassza ki a 'gh-pages' ágat, és mentse.
- A wiki a `https://{username}.github.io/{reponame}` címen lesz elérhető, például ehhez a repóhoz: `https://saqimtiaz.github.io/TW5-github-actions-example/`
  - Minden alkalommal, amikor módosításokat hajt végre a tárhelyen, a rendszer egy frissített TiddlyWiki fájlt készít és tesz közzé ezen az URL-en


### hibajavítások 

- verzióváltások 

```diff
  deploy:
-    runs-on: ubuntu-18.04
+    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
-     - uses: actions/setup-node@v2-beta
+     - uses: actions/setup-node@v3.0.0

```

- a yml deploy részénél hívott kód [readme-je alapján](https://github.com/peaceiris/actions-gh-pages) 


>If the action fails to push the commit or tag with the following error:
>
>```txt
>/usr/bin/git push origin gh-pages
>remote: Write access to repository not granted.
>fatal: unable to access 'https://github.com/username/repository.git/': The requested URL returned error: 403
>Error: Action failed with "The process '/usr/bin/git' failed with exit code 128"
>```
>
>Please add the write permission to the [`permissions.contents` in a workflow/job](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#permissions).
>
>```yaml
>permissions:
>  contents: write
>```
>
>Alternatively, you can [configure the default `GITHUB_TOKEN` permissions](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#configuring-the-default-github_token-permissions) by selecting read and write permissions.

- githubon létrehoztam a `gh-pages` branchen a `.nojekyll` állományt (ez számított valamit?)

