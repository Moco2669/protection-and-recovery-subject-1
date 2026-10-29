---
tip: pojam
aliases: [improper control of interaction frequency, missing rate limiting, unrestricted resource consumption]
izvor: CWE-799 Improper Control of Interaction Frequency; OWASP API Security Top 10:2023, API4:2023 i API6:2023
status: predlog
sloj: jezgro
---
# Nekontrolisana učestalost zahteva (improper control of interaction frequency)

## Definicija
Nekontrolisana učestalost zahteva je [[Slabost|slabost]] u kojoj [[Komponenta sistema|komponenta sistema]] ne ograničava koliko puta isto lice, uređaj ili nalog sme da ponovi neku radnju u određenom vremenu.

## Primer
Javna stranica za plaćanje aplikacije [[Fakturis]] ne ograničava broj pokušaja plaćanja. Prevaranti koji su kupili spisak ukradenih kartica otvaraju jednu fakturu i automatski probaju hiljade kartica, da bi saznali koje još rade. Svaki pokušaj ide preko PayNet-a, koji firmi naplaćuje naknadu po pokušaju i posle nekoliko dana privremeno blokira njen nalog zbog sumnje na prevaru. Proces naplate staje za sve korisnike.

Ista slabost postoji na prijavi: broj pokušaja prijave nije ograničen, pa napadač može automatski da pogađa lozinke korisnika.

## Napomene
- Primer sa karticama pokazuje kako napadač zloupotrebljava [[Spoljni servis|spoljni servis]] preko naše aplikacije: šteta nastaje kod PayNet-a i njegovih korisnika, a posledice snosi Fakturis.
- OWASP ovu slabost naziva *unrestricted resource consumption*. Tu reč *resource* označava procesorsko vreme, memoriju ili plaćene pozive, a ne [[Resurs]] u smislu ove baze.
