---
tip: pojam
aliases: [web application, aplikacija, API]
izvor: CIS Critical Security Controls v8, Glossary, "application"
status: predlog
sloj: temelj
---
# Web aplikacija (web application)

## Definicija
Web aplikacija je softverska komponenta sistema koja preko mreže prima HTTP zahteve korisnika ili drugih programa, obrađuje ih prema poslovnoj logici organizacije i vraća odgovore.

## Primer
Web aplikacija [[Fakturis]] se izvršava na aplikacionom [[Server|serveru]] i ima tri dela: korisnički deo (registracija, prijava, izdavanje faktura, evidencija kupaca), javnu stranicu za plaćanje fakture kojoj kupac pristupa preko linka i administratorski deo za podršku. Web frontend sa backendom komunicira preko REST API-ja. Aplikacija čita i menja podatke u [[Baza podataka|bazi podataka]] i upisuje PDF fakture u [[Skladište dokumenata|skladište dokumenata]].

Deo aplikacije je i veza sa PayNet-om: kod koji šalje zahteve za naplatu potpisane API ključem i adresa `/api/paynet/obavestenje` na koju PayNet javlja ishod plaćanja. PayNet je servis druge firme, nije komponenta Fakturisa. Kartica kupca u sistem ne ulazi.

Kontraprimer: nginx na istom serveru takođe prima HTTP zahteve, ali ih samo prosleđuje aplikaciji i ne sadrži poslovnu logiku firme. On je deo serverskog okruženja.

## Napomene
- Web aplikacija je jedina komponenta firme kojoj svako sa interneta može da pošalje zahtev, pa je izložena najvećem broju napadača.
- U [[Fakturis]] adresa `/api/fakture/{id}` vraća fakturu svakom prijavljenom korisniku, bez provere da li je njegova. Obaveštenje o uplati prihvata se bez provere da ga je poslao PayNet.
