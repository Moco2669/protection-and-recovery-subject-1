---
tip: pojam
aliases: [confidentiality]
izvor: ISO/IEC 27000:2018, 3.10 confidentiality
status: predavanje
sloj: temelj
---
# Poverljivost (confidentiality)

## Definicija
Poverljivost je [[Bezbednosno svojstvo|bezbednosno svojstvo]] [[Resurs|resursa]] da informacije koje sadrži nisu dostupne niti otkrivene licima, sistemima ili procesima koji za to nisu ovlašćeni.

## Primer
Korisnik [[Fakturis|Fakturisa]], Pekara Zrno, otvara svoju fakturu na adresi `/fakture/1043` i iz radoznalosti menja broj u `1044`. Aplikacija prikazuje fakturu druge firme, sa imenom kupca i iznosom. Pekara nije ovlašćena da vidi tu fakturu, pa je poverljivost narušena.

Kontraprimer: Jelena iz podrške otvara istu fakturu jer je njen izdavalac poslao zahtev za ispravku. Jelena je za to ovlašćena, pa je poverljivost očuvana.

## Napomene
- Narušavanje poverljivosti ne menja resurs: faktura je i dalje tačna i dostupna. Zato se ono često dugo ne primećuje.
