---
tip: pojam
aliases: [data flow]
izvor: A. Shostack, Threat Modeling: Designing for Security, Wiley, 2014 (dijagram toka podataka)
status: predlog
sloj: temelj
---
# Tok podataka (data flow)

## Definicija
Tok podataka je prenos podataka od jedne [[Komponenta sistema|komponente sistema]] do druge, ili između komponente sistema i spoljnog lica, uređaja ili servisa preko [[Granica sistema|granice sistema]].

## Primer
Obaveštenje o uplati u firmi [[Fakturis]] putuje od PayNet-a preko interneta i mrežnog prolaza do web aplikacije, na adresu `/api/paynet/obavestenje`. Aplikacija zatim upisuje novi status fakture u bazu. To su dva toka podataka: prvi prelazi granicu sistema, a drugi je unutar nje. Pošto prvi tok dolazi od servisa kojim firma ne upravlja, aplikacija mora da proveri da ga je zaista poslao PayNet.

Kontraprimer: kabl između mrežnog preklopnika i aplikacionog servera nije tok podataka, nego mrežna komponenta kroz koju tokovi prolaze.

## Napomene
- Arhitektura sistema se u ovoj bazi opisuje kao skup komponenti i tokova podataka između njih. Uobičajeni prikaz je dijagram toka podataka (data flow diagram, DFD). Dijagram za Fakturis je u beleški konteksta.
- Tok ima smer. Zahtev za naplatu i obaveštenje o uplati su dva toka između istih komponenti, sa različitim podacima i različitim pretnjama.
