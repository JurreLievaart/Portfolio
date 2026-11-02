---
title: "Pneumatische besturingen"
date: 2026-10-02
summary: "Practicum Besturingstechniek: een volledig pneumatische besturing ontworpen met een WST-diagram, gesimuleerd in Fluidsim en gebouwd op een Festobord."
tags: [Pneumatiek, Besturingstechniek, Fluidsim, Festo]

cover: festobord.webp

images:
  - file: festobord.webp
    alt: "Festobord met pneumatische cilinders, ventielen en blauwe en witte slangen, opgebouwd volgens het ontwerp"
    caption: "De besturing nagebouwd op het Festobord"
  - file: fluidsim-simulatie.webp
    alt: "Fluidsim-schema van het overzetstation tijdens de simulatie, met onder druk staande leidingen in donkerblauw"
    caption: "Simulatie van het overzetstation in Fluidsim tijdens de cyclus"
  - file: wst-diagram.webp
    alt: "Zelf opgesteld WST-diagram met de bewegingen van cilinder A, B en C, de signalen en de commando's"
    caption: "Zelf opgesteld WST-diagram van het overzetstation"

pdfs:
  - file: verslag-pneumatische-besturingen.pdf
    title: "Volledig practicumverslag"
---

Practicum van het vak Besturingstechniek (BARS3a) aan TIS Delft. Het doel was een besturing te ontwerpen, te simuleren en te bouwen waarbij **alles pneumatisch** gebeurt: eindstandmelders, logische ventielen en geheugens bepalen samen de volgorde van de cilinderbewegingen.

## Aanpak

Het practicum bestond uit vier deelopdrachten:

1. Besturingsformules afleiden uit een gegeven WST-diagram van een persinstallatie voor lagerbussen.
2. Zelf een WST-diagram en de formules opstellen voor een overzetstation voor verpakkingen.
3. Dit ontwerp simuleren in Fluidsim.
4. Het ontwerp bouwen en testen op het Festobord.

## Het ontwerp: overzetstation

Het overzetstation heeft drie cilinders. Cilinder A (bistabiel) schuift een verpakking op de tiltafel en gaat terug. Cilinder B (bistabiel) heft de lift. Cilinder C (monostabiel) kiept de tafel en houdt dit 5 seconden vast. Daarna gaat eerst C terug en dan B.

Stappen met dezelfde eindstanden zijn te onderscheiden met **één ongelijkmaakgeheugen** (signaal q). Alleen het eerste commando bevat alle beginstand-elementen, zodat de installatie niet start als een cilinder verkeerd staat. De andere commando's hebben genoeg aan één of twee signalen. Door de formules eerst te vereenvoudigen waren weinig componenten nodig.

## Simulatie en bouw

De formules zijn één op één omgezet naar een Fluidsim-model, opgebouwd in drie lagen: de sensoren onderaan, de besturingslogica in het midden en de ventielen en cilinders bovenaan. Zo lopen er weinig lijnen kruiselings. Daarna heb ik hetzelfde model met dezelfde componenten op het Festobord gebouwd.

Bij het testen controleerde ik eerst de beginstand. Daarna zette ik de startknop aan en vergeleek ik de volgorde van de bewegingen met het WST-diagram. Tot slot zette ik de startknop midden in een cyclus uit, om te controleren dat de cyclus wordt afgemaakt en de installatie in de beginstand stopt.

## Foutzoeken

Twee problemen kwamen tijdens het bouwen naar voren:

- Een plakkend Q-ventiel. Na vervanging, en met hulp van de docent, kon ik de leidingen terugvolgen tot het ventiel.
- Een compressor die te hoog stond en voor onverwachte uitvoer zorgde. Met een smoorventiel werd dat opgelost, en later vond ik ook de oorzaak.

## Resultaat

Voor beide installaties zijn met een WST-diagram de besturingsformules opgesteld en vereenvoudigd. De Fluidsim-simulatie van het overzetstation volgde het WST-diagram, en het ontwerp is daarna op het Festobord gebouwd.
