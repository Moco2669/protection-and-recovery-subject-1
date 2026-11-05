---
tip: pojam
aliases: ["repudiation"]
izvor: "Microsoft, Microsoft Threat Modeling Tool threats, STRIDE model, https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats; FTN, RBS 04 Modelovanje pretnji, slajdovi 48–60. Definicija je parafraza; manifestacije po komponentama su obrazložena primena, ne doslovan tekst izvora."
---

# Poricanje izvršene radnje (repudiation)

## Definicija

Poricanje izvršene radnje je tip pretnje pri kojem učesnik osporava svoje učešće u izvršenoj radnji, a raspoloživi dokazi ne omogućavaju da se to učešće pouzdano utvrdi.

## Primer

Organizacija zahteva da se može pouzdano utvrditi ko je odobrio izmenu poslovnog dokumenta. Učesnik odobri izmenu, a kasnije poriče odobrenje. Ako komponenta ne stvara potreban dokaz ili dozvoljava njegovo nedozvoljeno menjanje bez otkrivanja, to su moguće ranjivosti koje otežavaju utvrđivanje odgovornosti. Sam zapis sa korisničkim imenom nije automatski dovoljan dokaz da je radnju izvršila određena osoba.

## Napomene

Učesnik može poricati da je zatražio, izvršio ili odobrio radnju, uključujući slanje ili prijem poruke. Dokazi treba da omoguće pouzdano povezivanje učesnika sa konkretnom radnjom koju želimo da potvrdimo.

Procesi stvaraju potrebne dokaze, a sistem za zapise i skladište zapisa podržavaju njihovo prikupljanje i čuvanje. Nedostajući, uklonjeni ili neovlašćeno izmenjeni zapisi mogu otežati dokazivanje. [[Narušavanje integriteta podataka]] može tako omogućiti naknadno poricanje.

Neporecivost je svojstvo koje se štiti, a poricanje je tip pretnje. Nedovoljno beleženje je mogući nedostatak koji otežava dokazivanje. Samo postojanje zapisa ne garantuje neporecivost.

[[Lažno predstavljanje]] može dovesti do pogrešnog pripisivanja radnje. Pouzdanost zaključka zato zavisi i od utvrđivanja identiteta i od zaštite dokaza o radnji.
