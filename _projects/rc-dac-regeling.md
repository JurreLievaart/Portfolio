---
title: "Geregelde RC-DAC"
date: 2026-10-02
summary: "Practicum Regeltechniek: een Arduino met RC-filter als digitaal-naar-analoog-omzetter (DAC), met een P- en PI-regelaar die de uitgang ook onder belasting op het setpoint houdt."
tags: [Regeltechniek, Arduino, PID, Elektronica]

cover: breadboard.webp

images:
  - file: breadboard.webp
    alt: "Breadboard met een Arduino-kabelbundel, twee drukknoppen, een potmeter, weerstanden en een condensator"
    caption: "De RC-DAC opgebouwd op een breadboard"
  - file: p-regelaar-zonder-last.webp
    alt: "Grafiek van setpoint, uitgang en stuursignaal in volt tegen de tijd, met eronder de regelfout; de uitgang volgt het setpoint na elke stap"
    caption: "P-regelaar (Kp = 1) zonder last: de uitgang volgt het setpoint"
  - file: fout-per-kp.webp
    alt: "Lijngrafiek van de absolute fout tegen Kp: de fout daalt van 31,68 bij Kp 0,5 naar 24,18 bij Kp 20"
    caption: "Absolute fout per Kp (P-regelaar, last van 30 kΩ)"

pdfs:
  - file: verslag-rc-dac.pdf
    title: "Volledig practicumverslag"
---

Practicum van het vak Regeltechniek (BARS2) aan TIS Delft. Een Arduino kan geen echte analoge spanning maken, alleen een PWM-signaal van 0 of 5 V. Met een RC-laagdoorlaatfilter wordt dat signaal gemiddeld tot een gelijkspanning tussen 0 en 5 V: een eenvoudige **DAC** (digitaal-naar-analoog-omzetter). Ik heb deze RC-DAC gebouwd en er een regelaar aan toegevoegd, zodat de uitgang ook onder belasting het setpoint volgt.

## Aanpak

Het practicum bestond uit vier deelopdrachten:

1. De schakeling en software opbouwen en in open-loop laten werken.
2. Meetdata in open-loop verzamelen en verwerken.
3. De regellus sluiten met een P-regelaar.
4. De regelaar tunen.

## De schakeling

Pin 9 van de Arduino geeft het PWM-signaal via een weerstand van 2,2 kΩ naar een condensator van 470 µF. De spanning over die condensator is de uitgang en wordt gemeten op een analoge ingang. Het setpoint komt van een potmeter. Met twee drukknoppen sluit ik een van twee lasten aan.

De tijdconstante van het filter is ongeveer 1 s, dus na ongeveer 5 s staat de uitgang op zijn eindwaarde. Een last vormt met de weerstand een spanningsdeler en verlaagt daardoor de versterking: zonder last is de maximale uitgang 5,00 V, met de last van 30 kΩ 4,66 V en met de last van 2,2 kΩ nog maar 2,50 V.

## Software

In de code van de docent heb ik vijf regels ingevuld: de afgeleiden van setpoint en uitgang, de fout, de integraal en de regelwet. Een valkuil bij het omrekenen tussen ADC-waarde, volt en PWM: zonder ".0" wordt 5/1023 een deling van gehele getallen en is de uitkomst 0.

## Meten en regelen

- **Open-loop:** de uitgang volgt elke stap volgens een eerste-orde laadcurve. Zonder last komt de uitgang op het setpoint uit.
- **P-regelaar (Kp = 1):** zonder last volgt de uitgang het setpoint binnen 1% en bereikt hij het setpoint na een stap binnen ongeveer 2 s, sneller dan in open-loop. Met de last van 30 kΩ blijft een offset van ongeveer 4–5% over (8% bij 5 V), wat binnen de eis van 15% blijft. Met de last van 2,2 kΩ is de offset 34% en komt de uitgang boven 2,5 V niet uit: de spanningsdeler laat dan hoe dan ook maximaal 2,5 V toe.
- **Tunen:** de Arduino testte automatisch meerdere instellingen en telde per test de absolute fout over de hele testserie op. Een hogere Kp geeft een kleinere fout, maar de winst wordt steeds kleiner. Het RC-circuit is een eerste-orde systeem en wordt daardoor niet instabiel. In overleg met de docent ben ik verdergegaan met Kp = 1000.
- **PI-regelaar:** bij Kp = 1000 verschilde de fout tussen de Ki-waarden maar 0,03 V·s, binnen de meetonnauwkeurigheid. Met zo'n hoge Kp is de offset al kleiner dan één ADC-stap, dus de I-actie heeft niets meer weg te regelen.

## Foutzoeken

Tijdens de opbouw bleef de uitgang steeds hangen op 1,75 V. Door onderdelen één voor één los te halen bleek de condensator kapot. Na vervanging werkte de schakeling.

## Resultaat

Met een PWM-signaal en een RC-filter is een werkende DAC gemaakt die in open-loop het setpoint volgt. Een P-regelaar met Kp = 1 maakt het systeem sneller en houdt zonder last de offset onder 1%, maar onder zware last blijft 34% offset over. Een hogere Kp verkleint de fout steeds verder. Bij dit eerste-orde systeem kan Kp zeer hoog worden zonder instabiliteit, en de I-actie voegt bij die Kp niets meetbaars toe.
