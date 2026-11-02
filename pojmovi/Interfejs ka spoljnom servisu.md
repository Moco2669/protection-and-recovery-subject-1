---
tip: pojam
aliases: [external service interface]
izvor: nema standardne definicije u ovom užem smislu; srodno: ISO/IEC/IEEE 12207, "interface", tačka na kojoj se elementi sistema susreću da bi sarađivali
status: prihvaćeno
sloj: temelj
---
# Interfejs ka spoljnom servisu (external service interface)

## Definicija
Interfejs ka spoljnom servisu je deo [[Softverski proizvod|softverskog proizvoda]] koji za jednu namenu određuje koje pozive proizvod šalje [[Spoljni servis|spoljnom servisu]] i koje odgovore prima, tako da isti deo proizvoda može da pozove bilo koji servis koji te pozive ispunjava.

## Primer
Interfejs za naplatu u proizvodu firme [[Fakturis]] određuje poziv kojim se traži naplata i odgovor sa ishodom. Proizvod kroz taj interfejs zove bilo koji od dva spoljna servisa za naplatu. Ako jedan ne odgovori, zove drugi.

Kontraprimer: pozivi kojima bi proizvod slao poštu bili bi drugi interfejs, jer je namena druga.

## Napomene
- Interfejs je deo proizvoda, ne posebna komponenta pored njega.
- To što firma drži dva servisa i što proizvod, kad jedan ne odgovori, zove drugi, nije deo definicije interfejsa. Interfejs samo omogućava zamenu.
