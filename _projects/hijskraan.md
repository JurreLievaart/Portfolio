---
title: "Hijskraan van vakwerk: ontwerp, bouw en test"
date: 2026-01-26
summary: "Teamproject waarin een hijskraan van aluminium en staal is ontworpen, berekend, gebouwd en getest. De kraan droeg de vereiste 70 kg en bezweek pas bij 145 kg."
tags: [Vakwerken, Sterkteleer, SolidWorks, Samenwerken]

cover: schaalmodel-karton.jpg

images:
  - file: schaalmodel-karton.jpg
    alt: "Grijs kartonnen schaalmodel van een kraan met schuine ligger, liggend op een groene snijmat"
    caption: "Kartonnen schaalmodel van een van de concepten"
  - file: krachtenevenwicht.webp
    alt: "Handgetekend krachtenoverzicht op ruitjespapier met rode en blauwe pijlen en de kracht in newton bij elke staaf"
    caption: "Handberekening: krachten per staaf in newton"
  - file: cad-isometrisch.webp
    alt: "Isometrisch CAD-model van een groen A-frame met bodemprofielen op een houten testplaat"
    caption: "CAD: isometrisch aanzicht van de bodem met A-frame"
  - file: werkelijkheid-onderstel.jpg
    alt: "Daadwerkelijk geproduceerde bodem van de kraan."
    caption: "Werkelijkheid: Geproduceerde bodem met A-frame"
  - file: cad-Totaal.jpg
    alt: "Totaal overzicht van de te bouwen kraan"
    caption: "CAD: Toaaloverzicht"
  - file: werkelijkheid-falen.jpg
    alt: "Faalpunt belicht na statische belasting van 145 kg"
    caption: "Werkelijkheid: Belichting faalpunt"
  
---

Leertaak werktuigbouwkunde in teamverband: ontwerp en bouw een demontabele hijskraan die een statische last van 70 kg draagt. De casus is opgezet met Mammoet, een wereldwijd bedrijf in zwaar hijsen, als opdrachtgever. In het team had ik de rol berekeningen. Elk subteam werkte de helft van de kraan uit en produceerde daarna het ontwerp van het andere subteam.

## Eisen

| Eis | Waarde |
|---|---|
| Statische belasting | 70 kg zonder bezwijken |
| Doorbuiging hoofdgiek | maximaal 80 mm bij 70 kg |
| Opbouw | twee delen, uit aluminium en staalplaat |
| Montage en demontage | maximaal 20 minuten |
| Verbindingen | minstens 80% standaard M4- of M5-bouten |
| Massa | maximaal 5 kg |

## Aanpak

1. **Concepten:** vier concepten geschetst en uitgewerkt tot kartonnen schaalmodellen. Daaraan zag ik snel waar een constructie onstabiel was.
2. **Berekeningen:** per concept de krachten in alle staven bepaald met de knooppuntenmethode, inclusief een 3D-uitwerking met eenheidsvectoren.
3. **Conceptkeuze:** de concepten gewogen tegen de eisen. Twee modellen bleken bijna gelijkwaardig, dus heb ik ze samengevoegd.
4. **Detailontwerp:** de kraan in tweeën gedeeld, uitgewerkt in SolidWorks en een knikberekening gemaakt voor de zwaarst belaste drukstaaf.
5. **Productie en test:** onderdelen geponst en geknipt, ontbraamd, geassembleerd en op een testopstelling belast.

## Ontwerp

Het uiteindelijke ontwerp combineert twee concepten. Een A-frame ondersteunt zichzelf: de achterste staven worden alleen op trek belast en het schuine A-frame in het midden alleen op druk. Boven op de schuine ligger heb ik een extra driehoek toegevoegd, naar het voorbeeld van een driehoekige vakwerkligger, om knik tegen te gaan. Die extra staven nemen in de berekening weinig kracht op, maar geven de lange ligger stijfheid.

De twee kraandelen zijn verbonden met drie M5-bouten die onderaan en bovenaan scharnieren vormen. Dit is een bewuste keuze: bij overbelasting kan de verbinding meegeven zonder dat de rest van de constructie wordt stukgetrokken.

## Productie

Voor de productie stelden we eerst samen een knipplan op, dat na goedkeuring is uitgevoerd. Daarna wisselden de subteams tekeningen en assemblageplannen uit, zodat elk team het ontwerp van het andere team bouwde. De staven zijn geponst en geknipt en daarna ontbraamd. Sleufgaten vingen kleine maatafwijkingen op, waardoor de onderdelen goed in elkaar pasten. Na drie ochtenden in de werkplaats was de kraan compleet. Met een nameetplan heb ik gecontroleerd dat de meeste onderdelen binnen de toleranties lagen.

## Test en resultaat

De kraan is op een testopstelling stapsgewijs belast.

- **Bij 70 kg** bleef de constructie stabiel en bleef de doorbuiging onder de toegestane 80 mm. Daarmee voldeed de kraan aan de eisen.
- **Bij 145 kg** bezweek de kraan, ruim twee keer de vereiste belasting.

Het bezwijken verliep in twee stappen. Eerst boog een staaf aan de voorzijde naar binnen door een hoog buigend moment in combinatie met een lage torsiestijfheid. Daarna scheurden twee aluminium trekstaven aan de achterzijde uit bij de boutgaten onderaan. De oorzaken zijn hoge lokale spanningen rond de gaten, uitscheuren van het aluminium onder trekbelasting en een krachtverdeling over de verbinding die niet gelijkmatig genoeg was.

## Wat ik leerde

- Een schaalmodel van karton laat zwakke plekken en instabiliteit zien voordat je gaat rekenen.
- Sleufgaten maken assemblage makkelijker, maar de speling in de bouten kost stijfheid, vooral in de verticale staanders.
- De zwakste schakel zat in de boutverbindingen. Bij een volgende versie zou ik de krachten over meer bouten of een grotere randafstand verdelen.
- Goede afspraken over de koppelvlakken tussen de twee kraandelen zijn net zo belangrijk als de berekening zelf.
