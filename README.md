# Kategóriáda

Minimalistická denná slovná hra v HTML, CSS a JavaScripte. Nepotrebuje backend, databázu, registráciu ani platené API.

## Súbory

- `index.html` – používateľské rozhranie a herná logika
- `catalog.json` – 31 denných výziev na október 2026
- `logo.svg` – jednoduché logo Kategóriády

## Spustenie lokálne

Prehliadače z bezpečnostných dôvodov často nedovolia načítať `catalog.json` cez `file://`. Spusti preto jednoduchý lokálny server v priečinku projektu:

```bash
python -m http.server 8000
```

Potom otvor [http://localhost:8000](http://localhost:8000).

Alternatívne môžeš použiť rozšírenie Live Server v editore Visual Studio Code.

## Publikovanie na GitHub Pages

1. Vytvor nový GitHub repozitár, napríklad `Kategoriada`.
2. Nahraj do koreňa repozitára všetky tri súbory: `index.html`, `catalog.json` a `logo.svg`.
3. V repozitári otvor **Settings → Pages**.
4. V časti **Build and deployment** vyber **Deploy from a branch**.
5. Vyber vetvu `main` a priečinok `/(root)`, potom ulož.
6. Po dokončení nasadenia otvor adresu, ktorú GitHub Pages zobrazí, napríklad `https://username.github.io/Kategoriada/`.

Všetky cesty k súborom sú relatívne (`./catalog.json`, `./logo.svg`), takže fungujú aj v podpriečinku repozitára. Na vlastnú doménu prejdi do **Settings → Pages → Custom domain**, zadaj doménu a nastav DNS podľa pokynov GitHubu. Zapni HTTPS, keď bude dostupné.

## Ako funguje hra

- Dátum sa určuje podľa časového pásma `Europe/Bratislava`.
- Každý nesprávny tip odhalí presne jedno ďalšie slovo.
- Odpovede sa normalizujú: ignoruje sa diakritika, veľkosť písmen, nadbytočné medzery a bežná interpunkcia. Ďalšie prijateľné odpovede sú v poli `acceptedAnswers`.
- Každý dátum má samostatný uložený stav. Po vyriešení, vzdaní sa alebo desiatich nesprávnych tipoch sa daná séria uzavrie.
- Výsledky sa ukladajú iba do `localStorage` v aktuálnom prehliadači. Nesynchronizujú sa automaticky medzi zariadeniami ani prehliadačmi. Vymazanie dát webu ich môže odstrániť.
- Zdieľaný výsledok neobsahuje názov správnej kategórie.

## Pridávanie ďalších mesiacov

Do poľa `days` v `catalog.json` pridaj záznamy s jedinečným dátumom `YYYY-MM-DD`, kategóriou, poľom `acceptedAnswers` a presne desiatimi položkami v `words`. Rozhranie kalendára v tejto verzii zobrazuje október 2026; pri pridaní ďalšieho mesiaca treba rozšíriť aj kalendár v `index.html`.

## Poznámka k denným odpovediam

Keďže ide o statickú webovú stránku bez servera, `catalog.json` sa musí stiahnuť do prehliadača a technicky zvedavý návštevník si môže prezrieť aj budúce záznamy v zdrojovom súbore. Rozhranie však budúce dni zamyká a odpovede nezobrazuje. Skutočné utajenie budúcich riešení by vyžadovalo serverovú časť.
