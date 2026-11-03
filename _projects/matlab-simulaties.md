---
title: "MATLAB- en Simulink-simulaties"
date: 2026-06-10
summary: "Drie kleine simulatieopdrachten in MATLAB en Simulink: warmteverlies door ventilatie, een parachutesprong en een verwarmingsregeling."
tags: [MATLAB, Simulink, Simulatie, Warmteoverdracht]

cover: parachute-snelheid.webp

images:
  - file: ventilatie-model.webp
    alt: "Simulink-blokschema met constanten voor hoogte, breedte, lengte en ventilatievoud die worden vermenigvuldigd en door 3600 gedeeld, plus een tweede berekening met temperatuurverschil, luchtdichtheid en soortelijke warmte; uitgangen zijn volumedebiet en warmteverlies"
    caption: "Opdracht 1: Simulink-model voor volumedebiet en warmteverlies"
  - file: parachute-model.webp
    alt: "Simulink-blokschema van de parachutesprong met zwaartekracht, massa, luchtweerstand, twee integratoren, een schakelaar tussen vrije val en geopende parachute en een stopblok bij hoogte nul"
    caption: "Opdracht 2: Simulink-model van de parachutesprong"
  - file: parachute-snelheid.webp
    alt: "Grafiek van snelheid tegen tijd: de snelheid loopt op tot ongeveer 70 meter per seconde, valt na ongeveer 35 seconden terug naar circa 6 meter per seconde en blijft daarna constant tot 83 seconden"
    caption: "Opdracht 2: snelheid tegen tijd, met het openen van de parachute na ongeveer 35 s"
  - file: verwarming-model.webp
    alt: "Simulink-blokschema van de verwarmingscasus met twee subsystemen voor water en lucht, een aan/uit-regelaar, scopes en displays met 55,74 graden Celsius, 1505 watt en 192,3 kilowattuur"
    caption: "Opdracht 3: Simulink-model van de verwarmingscasus met de resultaten"
  - file: verwarming-studiotemperatuur.webp
    alt: "Grafiek van de studiotemperatuur over een week: de temperatuur schommelt snel tussen ongeveer 18,5 en 21,5 graden Celsius rond de gewenste 20 graden, met een dagelijks terugkerend patroon"
    caption: "Opdracht 3: studiotemperatuur over een week (604.800 s)"
---

Drie kleine opdrachten uit het vak BARS 2 Simulation with Simulink, waarin ik fysische situaties omzette naar een model in MATLAB en Simulink. Per opdracht staan de parameters in een MATLAB-script en de berekening in een Simulink-model.

## 1. Warmteverlies door ventilatie

Een ruimte verliest warmte doordat warme binnenlucht door koude buitenlucht wordt vervangen. Het model rekent dat uit met twee stappen:

- **Volumedebiet:** lengte · breedte · hoogte van de ruimte · ventilatievoud, gedeeld door 3600 om van m³/uur naar m³/s te gaan.
- **Warmteverlies:** luchtdichtheid (1,21 kg/m³) · soortelijke warmte van lucht (1008 J/kgK) · volumedebiet · temperatuurverschil tussen binnen en buiten.

Ik heb het model ingesteld voor een ruimte van 5 × 4 × 2,5 m (50 m³) met een ventilatievoud van 2 per uur, een binnentemperatuur van 22 °C en een buitentemperatuur van −8 °C. Dat geeft een volumedebiet van 0,0278 m³/s (100 m³/uur) en, bij een temperatuurverschil van 30 K, een warmteverlies van ongeveer 1016 W.

## 2. Parachutesprong

Dit model simuleert de val van een parachutist. Met integratoren volgt uit de versnelling de snelheid en daaruit de afgelegde weg. De versnelling is de zwaartekracht (9,81 m/s²) min de luchtweerstand, gedeeld door de massa. De weerstand is 0,5 · ρ · Cw · A · v², eerst met de weerstandscoëfficiënt en het oppervlak van de vrije val (Cw = 1, A = 0,25 m²) en daarna met die van de geopende parachute (Cw = 1,5, oppervlak 24 m²). Op een instelbare hoogte schakelt het model over op de parachute, en de simulatie stopt zodra de parachutist de grond raakt.

Ik heb een parachutist van 75 kg gesimuleerd die op 2500 m hoogte springt en een parachute van 24 m² opent op 350 m hoogte. In de vrije val loopt de snelheid op tot ongeveer 70 m/s (250 km/h), waar luchtweerstand en zwaartekracht elkaar in evenwicht houden. Na het openen van de parachute, na ongeveer 35 s, zakt de snelheid in enkele seconden naar 5,8 m/s (21 km/h), onder de veilige landingssnelheid van 25 km/h. De hele sprong duurt 83,75 s.

## 3. Verwarmingscasus

Het derde model beschrijft een ruimte (een studio) met een radiator, over een hele week (604.800 s). Het thermodynamische basismodel met een water- en een luchtdeel is aangeleverd in het vak. [VERVANG: wat heb je zelf toegevoegd of ingesteld, bijvoorbeeld de regeling en de metingen.]

- **Regeling:** de gewenste temperatuur is 20 °C. Het verschil met de studiotemperatuur gaat naar een aan/uit-regelaar (relay) met een hysterese van ±1 °C, die de waterpomp van de radiator schakelt (water van 70 °C, 2,5·10⁻⁵ m³/s).
- **Omgeving:** de buitentemperatuur is een sinus met een periode van 24 uur en een gemiddelde van −4,5 °C (tussen −10 en +1 °C). De buren houden 18 °C aan en de ventilatie is 60 m³/uur.
- **Metingen:** het model laat het radiatorvermogen, de hoogste watertemperatuur en de totale energie (omgerekend van joule naar kWh) zien.

Uit de simulatie volgen een maximaal vermogen van 1505 W, een hoogste watertemperatuur in de radiator van 55,7 °C en een energieverbruik van 192,3 kWh per week. De studiotemperatuur schommelt rond de gewenste 20 °C, tussen ruwweg 18,5 en 21,5 °C, en die schommeling volgt het dagritme van de buitentemperatuur.

## Wat ik hiervan leerde

Ik heb geleerd hoe ik een fysische situatie omzet in een Simulink-model, van een eenvoudige formule tot een model met integratoren en een regelaar. Daarbij zag ik hoe de keuze van parameters, zoals de openingshoogte van de parachute of de schakelmarge van de thermostaat, het resultaat direct verandert.