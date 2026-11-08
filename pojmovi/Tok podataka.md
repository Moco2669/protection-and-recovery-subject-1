---
tip: pojam
aliases: [data flow]
izvor: Shostack, Experiences Threat Modeling at Microsoft, 2008, tabela 1, "data flow" ([PDF](https://shostack.org/files/papers/modsec08/Shostack-ModSec08-Experiences-Threat-Modeling-At-Microsoft.pdf))
status: predlog
sloj: temelj
---
# Tok podataka (data flow)

## Definicija
Tok podataka je prenos podataka od jednog elementa dijagrama toka podataka do drugog. Na dijagramu se prikazuje usmerenom strelicom. Strelica pokazuje smer prenosa, a njen opis može da navede koji se podaci prenose i kojim [[Protokol|protokolom]].

## Primer
Pri izdavanju fakture u firmi [[Fakturis]], korisnik šalje stavke fakture [[Softverski proizvod|softverskom proizvodu]]. Proizvod prenosi zapis fakture do [[Baza podataka|baze podataka]], a datoteku fakture do [[Skladište datoteka|skladišta datoteka]]. Svaki prenos je zaseban tok podataka.

Kontraprimer: mrežna veza između servera i [[Baza podataka|baze podataka]] sama po sebi nije tok podataka. Tok je prenos koji se odvija između elemenata, a mrežna veza je jedan od načina na koji može da se ostvari.

## Napomene
- U ovoj bazi jedan kraj toka je uvek [[Procesna jedinica|procesna jedinica]]. Drugi kraj može biti procesna jedinica, [[Skladište podataka|skladište podataka]] ili [[Spoljni entitet|spoljni entitet]].
- Tok može ići i od skladišta podataka ka procesnoj jedinici kada procesna jedinica čita sačuvane podatke.
- Na dijagramu se protokol i vrsta podataka navode kao opis toka; nisu posebni elementi dijagrama.
- Tok može da ulazi u modelovani sistem, izlazi iz njega ili se kreće između njegovih elemenata. Protokol i vrsta podataka mogu da se navedu uz strelicu.
- Tokovi koji prelaze [[Granica poverenja|granicu poverenja]] izdvajaju se radi bezbednosne analize.
- Tokovi su elementi [[Dijagram toka podataka|dijagrama toka podataka]], koji se koristi kao osnova za razmatranje slabosti, napada i bezbednosnih kontrola.
