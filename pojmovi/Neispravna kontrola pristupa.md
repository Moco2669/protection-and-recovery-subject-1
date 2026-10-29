---
tip: pojam
aliases: [broken access control, IDOR, insecure direct object reference]
izvor: OWASP Top 10:2025, A01:2025 Broken Access Control (https://owasp.org/Top10/2025/); CWE-639, CWE-862
status: predlog
sloj: jezgro
---
# Neispravna kontrola pristupa (broken access control)

## Definicija
Neispravna kontrola pristupa je [[Slabost|slabost]] u kojoj [[Komponenta sistema|komponenta sistema]] dozvoljava licu ili procesu radnju nad [[Resurs|resursom]] bez provere, ili uz pogrešnu proveru, da li mu [[Bezbednosni zahtev|bezbednosni zahtevi]] tu radnju dozvoljavaju.

## Primer
Adresa `/api/fakture/{id}` aplikacije [[Fakturis]] proverava samo da li je korisnik prijavljen, ali ne i da li faktura pripada njemu. Brojevi faktura idu redom, pa korisnik koji promeni broj u adresi čita tuđe fakture. Ovaj oblik slabosti, gde je dovoljno promeniti identifikator objekta u zahtevu, naziva se nebezbedna direktna referenca na objekat (insecure direct object reference, IDOR).

## Napomene
- Prijava utvrđuje ko je korisnik, a kontrola pristupa šta taj korisnik sme. Aplikacija iz primera ispravno prijavljuje korisnika, ali ne proverava šta sme.
- Prema OWASP Top 10:2025, ovo je najzastupljenija kategorija slabosti web aplikacija.
