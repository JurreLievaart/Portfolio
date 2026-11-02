# Mijn portfolio-website

Een simpele site met een homepagina, cv, projectenoverzicht (met foto's en pdf's per project) en contactpagina. Gemaakt voor **GitHub Pages**: je hoeft niets te installeren en er is geen JavaScript nodig.

## Mapindeling

```
_config.yml                 Naam, contactgegevens en menu
index.html                  Homepagina
cv.html                     CV-pagina
projecten.html              Projectenoverzicht
contact.html                Contactpagina
_projects/                  Eén tekstbestand per project
assets/projects/<project>/  Foto's en pdf's per project
assets/cv.pdf               Je cv als download
assets/css/styles.css       Alle opmaak
_layouts/ en _includes/     Gedeelde onderdelen (header, footer, projectlijst)
```

## 1. Eerst invullen

Zoek in alle bestanden naar `[VERVANG]`. Dat is voorbeeldtekst die jij moet vervangen door je eigen gegevens:

- `_config.yml`: naam, beschrijving, e-mailadres, eventueel LinkedIn en GitHub
- `index.html`, `cv.html`, `projecten.html`, `contact.html`: de teksten
- `assets/cv.pdf`: vervang door je eigen cv (zelfde bestandsnaam)
- `_projects/voorbeeld-project.md` en `assets/projects/voorbeeld-project/`: pas aan of verwijder beide zodra je eigen projecten klaarstaan

## 2. Online zetten op GitHub Pages

1. Maak op github.com een nieuwe repository. Noem je die `jouwgebruikersnaam.github.io`, dan wordt je site `https://jouwgebruikersnaam.github.io`. Bij een andere naam (bijv. `portfolio`) wordt het `https://jouwgebruikersnaam.github.io/portfolio`; zet dan `baseurl: "/portfolio"` in `_config.yml`.
2. Upload alle bestanden en mappen uit deze map (**Add file → Upload files**; je kunt mappen slepen). Let op: mappen die met een underscore beginnen (`_layouts`, `_projects`, `_includes`) moeten ook mee.
3. Ga naar **Settings → Pages**. Kies bij *Source* **Deploy from a branch**, kies de branch `main` en de map `/ (root)`, en klik op Save.
4. Na een à twee minuten staat de site online. Zie je een fout, kijk dan bij het tabblad **Actions** van je repository: daar staat wat er misging.
5. Vul daarna bij `url` in `_config.yml` je siteadres in (bijv. `https://jouwgebruikersnaam.github.io`). Dat is nodig voor een kloppende sitemap en canonical-links.

## 3. Een nieuw project toevoegen

1. **Map maken:** maak in `assets/projects/` een map met een korte naam zonder spaties of hoofdletters, bijv. `rem-ontwerp`.
2. **Bestanden uploaden:** zet je foto's en pdf's in die map.
3. **Tekstbestand maken:** kopieer `_projects/voorbeeld-project.md` naar `_projects/rem-ontwerp.md`. **De bestandsnaam moet gelijk zijn aan de mapnaam.**
4. **Invullen:** pas de titel, datum, samenvatting, foto's (`images`) en pdf's (`pdfs`) bovenin aan en schrijf onder de tweede streepjeslijn de beschrijving.
5. **Opslaan (commit):** na een à twee minuten staat het project online, automatisch bovenaan het overzicht. De volgorde volgt de `date`.

Foto's en pdf's die je niet in de lijst `images` of `pdfs` zet, worden niet getoond. Een project zonder foto's of pdf's werkt ook: laat die onderdelen dan weg. Staat er een dubbele punt in een tekst (bijv. een titel), zet de tekst dan tussen aanhalingstekens.

## 4. Foto's en pdf's klein houden

Een snelle site begint bij kleine bestanden.

- **Foto's:** maximaal circa 1600 pixels breed, formaat WebP of JPG, liefst onder 300 KB. Op [squoosh.app](https://squoosh.app) kun je dit gratis in je browser doen.
- **Pdf's:** liefst onder 5 MB. Bestanden uploaden via de GitHub-website kan tot ongeveer 25 MB per bestand.
- **Bestandsnamen:** kleine letters, geen spaties (`rem-schets-1.webp`).
- **Alt-tekst:** beschrijf elke foto kort. Dat helpt slechtzienden en zoekmachines.

## 5. Zelf een pagina toevoegen

Kopieer bijvoorbeeld `contact.html` naar een nieuw bestand, pas de bovenkant (`title`, `description`, `permalink`) en de inhoud aan, en zet de pagina in `nav` in `_config.yml` om hem in het menu te krijgen.

## 6. Lokaal bekijken (optioneel)

Dit hoeft niet; je kunt ook gewoon uploaden en op GitHub kijken. Wil je wel lokaal testen: installeer Ruby, voer `gem install jekyll webrick` uit en start de site met `jekyll serve` in deze map. Open daarna `http://localhost:4000`.

## Over de keuzes

- Contact gaat via een e-maillink in plaats van een formulier: een formulier heeft een backend of externe dienst nodig.
- Er zijn geen externe lettertypen, scripts, trackers of afbeeldingen van derden.
