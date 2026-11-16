# KELLIXÍR SHIFT — v8 polishing build

## Soubor
Otevřete `KELLIXIR_SHIFT_v8.html` v prohlížeči. Funguje jako samostatná lokální aplikace bez instalace a bez externích knihoven. Změny se ukládají jen do místního úložiště prohlížeče. V8 používá vlastní klíč úložiště, takže nemaže data z předchozích verzí.

## Co je nové
- Jednotná vizuální paleta: oxidovaná měď / patina, hluboký smaragd, jantar, bordó a teplý lněný základ.
- Mírnější typografické váhy a vyšší kontrast drobných popisků.
- Odstraněny dlouhé instruktážní a marketingové poznámky z obrazovek.
- Kalendář: malé zarovnané plus v levém spodním rohu, výchozí měsíc, přepínatelný týden.
- Manažerský přehled: fronta k vyřízení, propojuje čekající uzávěrky, akce potřebující posily a žádosti.
- Finanční uzávěrka: živý výpočet tržby, podílu, dýšek, rozdělení mezi zaměstnance, očekávané hotovosti a terminálu.
- Zabránění přeplatkům, záporné očekávané hotovosti a schválení nevysvětlených rozdílů.
- Schválená uzávěrka blokuje úpravy rozpisu v daném dni včetně automatického obsazení.
- Akce mají ochrany proti duplicitnímu vytváření posil a nesouladu s již vytvořenými směnami.
- Zrychlení: vykresluje se jen aktuálně otevřená sekce, ostatní obrazovky se nepočítají zbytečně.

## Role
**Manažer:** měsíční/týdenní rozpis, návrh obsazení, úpravy směn, žádosti, tým, akce, posily, uzávěrky, výplaty, schválení, export CSV.

**Obsluha:** přehled, moje směny, dostupnost, žádosti o volno a převzetí směny, uzávěrka provozního dne s přiřazenou směnou, vlastní vyúčtování. Manažerské sekce nejsou v této roli dostupné.

## Finanční výpočty v prototypu
- Tržba = hotovostní + karetní tržba zadaná **bez dobrovolných dýšek**.
- Fond 4 % = čtyři procenta takto zadané tržby. Je předpokládáno, že tyto dvě tržby používají stejnou účetní bázi. Zda jde o částky s DPH nebo bez DPH, musí provoz potvrdit při implementaci.
- Dobrovolné dýško hotově a dýško kartou se evidují zvlášť.
- Rozdělení podle naplánovaných hodin je **model**, nikoli evidence skutečně odpracovaného času ani výplatní páska.
- Očekávaná hotovost = počáteční stav + hotovostní tržba + dýška přidaná do kasy − hotovostní výplaty − ostatní hotovostní výdaje.
- Očekávané transakce terminálu = karetní tržba + karetní dýška.
- Vyplaceno převodem není pohybem hotovosti v kase.
- Schválená uzávěrka uchovává snímek vypočtených částek.

## Testování
- Proveden Playwright regresní test: vytvoření, úprava, smazání směny, časový přepínač, akce, generování bez duplicit, kasa, 4% podíl, schválení, zámek, role, dostupnost, žádosti, CSV.
- Extra testy: odmítnutí přeplatku, záporné kasy, nevysvětleného rozdílu, ochrana navázaných směn událostí, zaměstnanec bez směny nemůže uzavřít den.
- Kontrola 10 šířek 320–1440 px, bez přetékání hlavní stránky.
- Výkonnostní mikrobenchmark lokálního prohlížeče (36 přepnutí, 6 warm-up): medián v7 15,4 ms, v8 2,8 ms. Výsledek závisí na zařízení a datech.

## Omezení dema
Prototyp není online pokladní ani účetní systém. Nemá reálné přihlašování, serverové ověřování rolí, synchronizaci mezi zaměstnanci, napojení POS/terminálu, audit na serveru, ani reálnou docházku. V ostrém provozu musí role, uzávěrky a zápisy výplat vynucovat backend a účetní postupy musí ověřit provoz s účetní. **Do lokálního dema nezadávejte reálné citlivé finance ani osobní údaje.**

## Podklady pro workflow uzávěrky
- Toast Support: https://support.toasttab.com/en/article/Shift-Review-Checklist-for-Employees-and-Managers
- Toast Support: https://support.toasttab.com/en/article/Cash-Drawer-and-Shift-Review-Troubleshooting
- Square for Restaurants Cash Management Guide: https://assets.ctfassets.net/gc4s9mi2asix/7ctDMCfJUpq7ynJZyA2FtK/7d4c434941a5abb5068509c6aa32b36c/Square_for_Restaurants_Setup_Guide.pdf
