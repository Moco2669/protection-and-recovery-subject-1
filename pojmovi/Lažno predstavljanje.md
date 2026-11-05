---
tip: pojam
aliases: ["spoofing"]
izvor: "Microsoft, Microsoft Threat Modeling Tool threats, STRIDE model, https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats; FTN, RBS 04 Modelovanje pretnji, slajdovi 48–60. Definicija je parafraza; manifestacije po komponentama su obrazložena primena, ne doslovan tekst izvora."
---

# Lažno predstavljanje (spoofing)

## Definicija

Lažno predstavljanje je tip pretnje pri kojem napadač nastupa pod identitetom drugog učesnika ili komponente, tako da primalac prihvati pogrešno poreklo zahteva, odgovora ili podataka.

## Primer

Sistem organizacije treba da prihvata zahteve za izmenu poslovnog dokumenta samo od njegovog ovlašćenog korisnika. Napadač se predstavi kao taj korisnik, a softverski proizvod prihvati njegov zahtev pod tuđim identitetom. Ako proizvod uspostavlja identitet bez potrebne ispravne provere, ta osobina predstavlja ranjivost koja omogućava lažno predstavljanje. Da li je izmena zatim dozvoljena zavisi i od provere prava pristupa.

## Napomene

Softverski proizvod može prihvatiti zahtev pod tuđim identitetom ili odgovor procesa koji se lažno predstavlja kao očekivani servis. Tokom razmene proverava se identitet učesnika i poreklo poruka na krajnjim komponentama.

Proces može pristupiti lažnom servisu baze umesto očekivanom. U tom slučaju lažira se identitet servisa koji omogućava pristup skladištu. I čovek može biti obmanut predstavljanjem napadača kao proizvoda, servisa ili druge osobe.

Lažno predstavljanje odnosi se na prihvaćeni identitet, a [[Dobijanje prevelikih privilegija]] na sticanje nedozvoljenih mogućnosti. Obe pretnje mogu biti povezane u istom napadu.

Neispravna autentifikacija je mogući tip ranjivosti koji omogućava lažno predstavljanje.
