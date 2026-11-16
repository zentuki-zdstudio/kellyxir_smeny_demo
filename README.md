# KELLIXÍR SHIFT — interaktivní ukázka

Ukázka interní aplikace pro plánování směn, provozní akce, uzávěrky a tým Kellixíru.

## Odkaz na demo

Po zapnutí GitHub Pages bude aplikace přístupná na adrese ve tvaru
`https://UZIVATEL.github.io/REPOZITAR/`.

## Nasazení na GitHub Pages

1. Rozbal ZIP.
2. V existujícím repozitáři otevři **Add file → Upload files**.
3. Nahraj **obsah** této složky do kořene repozitáře (ne složku jako celek).
   Musí tam být `index.html` a podsložka `assets`.
4. Potvrď **Commit changes**.
5. Otevři **Settings → Pages**.
6. Nastav **Build and deployment → Deploy from a branch**,
   větev `main`, adresář `/(root)` a dej **Save**.
7. Po zveřejnění zkontroluj odkaz uvedený na stránce Pages.

Pokud už je Pages nastavené, stačí nahrát soubory a uložit změny.
Pokud repo používá jinou větev než `main`, vyber odpovídající větev.

## Složky

- `index.html` — vstupní soubor pro GitHub Pages
- `assets/styles.css` — vizuální styly
- `assets/app.js` — funkční interaktivní demo (bez serveru)
- `assets/favicon.svg` — ikona aplikace
- `previews/` — screenshoty pro prohlížení a prezentaci
- `docs/TECHNICKE_POZNAMKY.md` — stávající funkce, omezení, logika výpočtů
- `FEEDBACK_PRO_MANAGERA.md` — podklad pro strukturovanou zpětnou vazbu

## Důležité

**Jde pouze o lokální prototyp pro ukázku.** Data se ukládají do `localStorage`
prohlížeče. Mezi zařízeními se nesynchronizují, přepínač rolí není přihlášení
a pokladní ani výplatní logika není napojená na skutečný provoz.

Nezadávejte skutečné osobní údaje, finance, přístupové tokeny ani hesla.
GitHub Pages neslouží jako chráněný interní systém; samotná stránka může být
veřejně dostupná a `noindex` není přístupové omezení.

Pro ostrý systém budou potřeba autentizace, databáze, serverová oprávnění,
audit změn, bezpečné API a provozní testování. Kód je určen k posouzení
demonstrace, nikoli k přímému použití jako produkční pokladní systém.
