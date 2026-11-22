---
tip: pojam
aliases: ["denial of service"]
izvor: "Microsoft, Microsoft Threat Modeling Tool threats, STRIDE model, https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats; FTN, RBS 04 Modelovanje pretnji, slajdovi 48–60. Definicija je parafraza; manifestacije po komponentama su obrazložena primena, ne doslovan tekst izvora."
---

# Narušavanje dostupnosti resursa (denial of service)

## Definicija

Narušavanje dostupnosti resursa je tip pretnje pri kojem napadač onemogućava ili otežava ovlašćenom učesniku korišćenje podataka, funkcija ili usluga u obimu i vremenu određenim bezbednosnim zahtevima.

## Primer

Ovlašćeni korisnici treba da mogu da koriste poslovnu funkciju proizvoda. Napadač pokrene toliko obrada da drugi korisnici ne mogu da je koriste u zahtevanom vremenu. Nekontrolisana potrošnja kapaciteta ili pogrešno podešena ograničenja mogu predstavljati ranjivost koja omogućava tu pretnju. Samo postojanje sistema za ograničavanje nije dokaz da je on ispravno podešen.

## Napomene

**Procesna jedinica.** Obrada se usporava ili prekida, a zahtevi ostaju neobrađeni. Uzrok koji napadač iskorišćava može biti iscrpljivanje kapaciteta, greška koja obara proces ili neispravno ograničavanje rada.

**Tok podataka.** Prenos se prekida, blokira ili odlaže tako da komponente ne dobijaju potrebne podatke na vreme. Posmatramo dostupnost konkretne razmene, a ne samo to da li uređaj radi.

**Skladište podataka.** Ovlašćena komponenta ne može da pročita ili upiše potrebne podatke. Napadač može iscrpeti prostor, zadržati nedozvoljeno dugo zauzeće ili učiniti podatke nedostupnim. Mehanizam i uslovi utvrđuju se za konkretnu komponentu.

Pretnja obuhvata i degradaciju potrebne usluge, ne samo potpuni prekid rada.

Nekontrolisana potrošnja resursa je mogući tip ranjivosti, slanje opterećujućih zahteva radnja napada, a nemogućnost dozvoljenog korišćenja posledica.

Slučajni kvar sam po sebi nije napad. Ovde razmatramo narušavanje koje napadač može izazvati.

