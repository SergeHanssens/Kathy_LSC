# Kathy_LSC — leesmateriaal

Oefentools en afdrukbladen voor leerlingen op leesniveau M3–E3, opgebouwd rond de klank-tekenkoppeling van Taal in Blokjes.

Alles is statisch: losse HTML-bestanden zonder build, zonder framework en zonder externe bronnen. Elke tool werkt offline zodra de pagina geladen is, ook op een smartbord zonder netwerk.

**Online:** https://sergehanssens.github.io/Kathy_LSC/KLSCflitskaarten/

---

## Structuur

```
/
├── index.html              overzichtspagina met alle tools en materiaal
├── .nojekyll               zonder dit bestand negeert GitHub Pages mappen met _
├── assets/
│   ├── stijl.css           stijl van de overzichtspagina (niet van de tools)
│   └── favicon.svg
├── apps/
│   ├── flitsklanken/
│   │   └── index.html      klanken flitsen in de juiste kleur
│   └── leestempo/
│       └── index.html      metronoom, klankblokjes en timer
└── materiaal/
    ├── leesuur-afdrukbladen.pdf
    ├── lesvoorbereiding-leesuur-M3-E3.md
    ├── vervolgles-witte-klankgroepen.pdf
    └── vervolgles-witte-klankgroepen.md
```

Elke tool zit in een eigen map onder `apps/` met de app als `index.html`. Daardoor is de url kort en zonder bestandsextensie: `…/apps/flitsklanken/` in plaats van `…/apps/flitsklanken.html`.

---

## GitHub Pages aanzetten

Eenmalig, in de repo op github.com:

1. **Settings → Pages**
2. Bij *Source*: **Deploy from a branch**
3. Branch: **main**, map: **/ (root)** → *Save*

Na een minuut staat de site op `https://sergehanssens.github.io/Kathy_LSC/KLSCflitskaarten/`. Elke push naar `main` publiceert automatisch opnieuw.

---

## Een nieuwe tool toevoegen

1. Maak `apps/<naam>/index.html` met het volledige, zelfstandige HTML-bestand erin.
2. Zet eventuele afbeeldingen of data in diezelfde map, en verwijs er relatief naar (`./plaatje.png`). Geen verwijzingen naar bestanden buiten de map, dan blijft de tool los bruikbaar.
3. Voeg in `index.html` één kaartblok toe:

```html
<a class="kaart" href="apps/<naam>/">
  <span class="vlag" style="background:#f0704a"></span>
  <h3>Naam van de tool</h3>
  <p>Eén of twee zinnen over wat hij doet.</p>
  <span class="meta">Voor het smartbord &middot; werkt zonder internet</span>
</a>
```

De kleur van `.vlag` mag je kiezen uit de zes kleuren hieronder.

---

## Afspraken die de tools draaiend houden

Deze staan hier omdat ze al een keer misgelopen zijn op een iPad en op een Android-telefoon.

- **Geen externe bronnen.** Geen CDN, geen Google Fonts, geen afbeeldingen van elders. Alles in het bestand of in de eigen map.
- **Geen CSS-variabelen**, geen `inset:` en geen `gap:` tussen flexitems. Oudere tablet- en telefoonbrowsers kennen die niet en tonen dan een stukgelopen pagina.
- **JavaScript in de oude schrijfwijze**: `var` in plaats van `let`/`const`, gewone functies in plaats van arrow functions, `"a" + b` in plaats van template literals. Eén onbekende schrijfwijze en het hele script draait niet meer, zonder foutmelding.
- **Ontwerp voor een smal scherm.** Bovenaan hoogstens drie of vier knoppen; de rest achter een instellingenknop. Anders blijft er op een telefoon geen hoogte over voor de inhoud zelf.
- **Nooit een `.html` als bijlage doorsturen.** Op een telefoon of tablet opent zo'n bijlage in een voorbeeldvenster dat geen JavaScript uitvoert, en dan lijkt de tool stuk. Stuur altijd de link naar de gepubliceerde pagina door.

---

## De kleuren van Taal in Blokjes

| Kleur | Wat | Hex |
|---|---|---|
| groen | korte klinker | `#7dc470` |
| geel | lange klinker | `#ffe24e` |
| rood | tweetekenklank | `#f0704a` |
| wit | klankgroep (`aai ooi oei`, `eeuw ieuw uw`) | `#ffffff` |
| oranje | doffe klank | `#f7a928` |
| blauw | medeklinker | `#63c4ee` |

Donkere letterkleur op alle blokjes: `#14222c`. Achtergrond van de tools: `#132029`.

---

## Bestaande tools

### apps/flitsklanken

De 48 klanken van de klank-tekenkaart, elk in zijn eigen kleur.

- vijftien vaste reeksen (hele kaart, korte tegenover lange klinkers, tweetekenklanken, de witte klankgroepen, medeklinkers, en drie sporen die op de dicteeresultaten zijn afgestemd)
- eigen selectie: klanken aan- en uitzetten om precies te flitsen wat bij één leerling fout liep
- drie weergaven: letters in kleur, gekleurd blokje, of het hele scherm in de kleur
- *Raad de kleur*: de klank verschijnt grijs, de leerlingen zeggen de kleur, één tik toont het antwoord
- volgorde wordt elke ronde opnieuw geschud, zonder dat dezelfde klank twee keer na elkaar komt
- automatisch doorbladeren van 1 tot 8 seconden
- *Voorlezen na … s*: de klank verschijnt, na het gekozen aantal seconden (1 tot 15) wordt hij voorgelezen (met het steunwoord als dat aan staat), en daarna komt vanzelf de volgende klank. In *Raad de kleur* wordt de kleur getoond op het moment van voorlezen. Gebruikt de spraak van de browser zelf; staat er op het toestel geen Nederlandse stem, dan leest hij met de standaardstem. Een klank lezen is voor een computerstem moeilijk: korte klinkers en medeklinkers klinken vaak als de lettername, het steunwoord maakt het duidelijk.

### apps/leestempo

Drie onderdelen voor het leesuur.

- **Tempolezen**: metronoom met vijftien woordrijtjes, tempotrap per ronde en een foutenteller met tempo-advies. Spatiebalk start en stopt, de toets `f` telt een fout.
- **Klankblokjes**: typ een woord en het wordt in klanken verdeeld en ingekleurd. De indeling is bij te sturen door tussen twee blokjes te klikken; de kleur met de knop *Klik = kleur kiezen*. De automatische kleur is een voorstel, want open of gesloten lettergreep en de doffe `e` vallen niet met zekerheid te berekenen.
- **Herhaald lezen**: timer die juiste woorden per minuut berekent en de pogingen naast elkaar zet.

> **Nog te doen.** Deze tool is geschreven vóór de afspraken hierboven en gebruikt nog CSS-variabelen en de moderne JavaScript-schrijfwijze. Op een recente browser is dat geen probleem, maar op een ouder toestel kan hij stilvallen zoals dat bij flitsklanken gebeurde. Als hij ergens niet werkt, moet hij dezelfde omzetting krijgen.
