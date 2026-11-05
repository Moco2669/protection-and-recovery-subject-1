---
tip: pojam
aliases: ["tampering"]
izvor: "Microsoft, Microsoft Threat Modeling Tool threats, STRIDE model, https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats; FTN, RBS 04 Modelovanje pretnji, slajdovi 48–60. Definicija je parafraza; manifestacije po komponentama su obrazložena primena, ne doslovan tekst izvora."
---

# Narušavanje integriteta podataka (tampering)

## Definicija

Narušavanje integriteta podataka je tip pretnje pri kojem napadač izaziva izmenu, dodavanje ili uklanjanje podataka ili koda suprotno pravilima dozvoljenih promena.

## Primer

Podrška organizacije sme da pročita poslovni dokument, ali ne i da promeni njegov sadržaj. Napadač preko naloga podrške pošalje zahtev za izmenu, a proizvod ga izvrši. Pretnja je neovlašćena izmena dokumenta, dok je ranjivost pogrešno sprovođenje prava nad tim dokumentom. To što se identitet podrške ispravno utvrdio ne daje joj pravo izmene.

## Napomene

**Procesna jedinica.** Napadač izazove nedozvoljenu promenu podataka tokom obrade ili promenu koda i stanja od kojih obrada zavisi. Dozvoljeni unos nije napad samo zato što menja izlaz.

**Tok podataka.** Podaci se nedozvoljeno izmene, zamene ili dopune između slanja i prijema. Ranjivost može biti nepravilna provera autentičnosti i integriteta primljenih poruka.

**Skladište podataka.** Napadač menja zapise u bazi, sadržaj datoteka, kod u repozitorijumu ili dokaze u skladištu zapisa. Nedozvoljeno brisanje može istovremeno ugroziti i [[Narušavanje dostupnosti resursa|dostupnost]].

Pravila određuju koje promene su dozvoljene i ko sme da ih izvrši. Svaka promena nije narušavanje integriteta.

Izostanak potrebne provere integriteta može omogućiti da promena ostane neotkrivena. Ne objašnjava nužno kako je napadač dobio mogućnost izmene. Provera zahteva pouzdanu osnovu koju napadač ne može zameniti zajedno sa sadržajem.
