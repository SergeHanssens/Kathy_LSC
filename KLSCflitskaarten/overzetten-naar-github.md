# Overzetten naar GitHub — Kathy_LSC

Repo: `https://github.com/SergeHanssens/Kathy_LSC.git`
Bestand met de inhoud: `Kathy_LSC-repo.zip`

Alles is statisch. Geen build, geen npm, geen framework. De zip uitpakken in de repo en pushen volstaat.

---

## Wat erin zit

```
index.html                  overzichtspagina met alle tools en materiaal
README.md                   structuur, hostinginstructies, afspraken voor nieuwe tools
.nojekyll                   nodig voor GitHub Pages
.gitignore
assets/stijl.css            stijl van de overzichtspagina
assets/favicon.svg
apps/flitsklanken/index.html   klanken flitsen in de juiste kleur
apps/leestempo/index.html      metronoom, klankblokjes, timer
materiaal/                     vier bestanden: twee pdf's en twee lesvoorbereidingen
```

De tools zitten elk in een eigen submap, zoals gevraagd, zodat er later nog bij kunnen. De url wordt daardoor `…/apps/flitsklanken/` zonder bestandsextensie.

---

## Stap 1 — inhoud in de repo zetten

Als de repo nog leeg is of alleen een README bevat:

```bash
git clone https://github.com/SergeHanssens/Kathy_LSC.git
cd Kathy_LSC
unzip /pad/naar/Kathy_LSC-repo.zip -d .
git add -A
git commit -m "Leesmateriaal: overzichtspagina, flitsklanken, leestempo en afdrukbladen"
git push origin main
```

Bestaat er al een `README.md` in de repo en wil je die houden, pak de zip dan eerst elders uit en kopieer alles behalve `README.md` over.

Heet de hoofdbranch `master` in plaats van `main`, vervang dat dan in de laatste regel en verderop bij de Pages-instelling.

## Stap 2 — GitHub Pages aanzetten

In de repo op github.com:

1. **Settings → Pages**
2. *Source*: **Deploy from a branch**
3. Branch **main**, map **/ (root)** → *Save*

Na ongeveer een minuut staat de site op:

```
https://sergehanssens.github.io/Kathy_LSC/
```

De tools zelf op:

```
https://sergehanssens.github.io/Kathy_LSC/apps/flitsklanken/
https://sergehanssens.github.io/Kathy_LSC/apps/leestempo/
```

## Stap 3 — nakijken

- Opent de overzichtspagina, en werken de vier links naar `materiaal/`?
- Opent `apps/flitsklanken/` en verschijnt er meteen een gekleurde klank?
- Op een telefoon: staat er bovenaan één knop **⚙ Instellingen** in plaats van een muur van knoppen?

Als de pagina wel laadt maar de stijl ontbreekt, ontbreekt `.nojekyll` of staat Pages op de verkeerde map.

---

## Aandachtspunten

- **Niets toevoegen dat van buitenaf laadt.** Geen CDN, geen Google Fonts, geen externe afbeeldingen. De tools moeten op een smartbord zonder netwerk blijven werken.
- **`.nojekyll` niet weggooien.** Zonder dat bestand negeert GitHub Pages mappen die met een underscore beginnen, en dat breekt later stilletjes iets.
- **Geen `.html` als bijlage doorsturen naar leerkrachten.** Op een telefoon of tablet opent zo'n bijlage in een voorbeeldvenster dat geen JavaScript uitvoert, en dan lijkt de tool stuk. Altijd de link naar de gepubliceerde pagina sturen.
- **Openstaand punt:** `apps/leestempo/index.html` is geschreven vóór de compatibiliteitsafspraken en gebruikt nog CSS-variabelen en de moderne JavaScript-schrijfwijze. Op recente browsers is dat geen probleem, maar op een ouder toestel kan hij stilvallen zoals dat bij flitsklanken gebeurde. `apps/flitsklanken/index.html` is wel al omgezet en kan als voorbeeld dienen.
- **Licentie.** Er staat er nog geen in de repo. Zonder licentiebestand geldt standaard "alle rechten voorbehouden" en mag niemand het formeel hergebruiken. Als het vrij deelbaar moet zijn voor collega's, is CC BY-SA 4.0 een logische keuze voor lesmateriaal.

---

## Een nieuwe tool toevoegen

1. `apps/<naam>/index.html` aanmaken met het volledige zelfstandige HTML-bestand.
2. In `index.html` één kaartblok bijzetten:

```html
<a class="kaart" href="apps/<naam>/">
  <span class="vlag" style="background:#f0704a"></span>
  <h3>Naam van de tool</h3>
  <p>Eén of twee zinnen over wat hij doet.</p>
  <span class="meta">Voor het smartbord &middot; werkt zonder internet</span>
</a>
```

3. Committen en pushen. Pages publiceert automatisch opnieuw.

De kleuren voor `.vlag` staan in de README, samen met de volledige afspraken voor nieuwe tools.
