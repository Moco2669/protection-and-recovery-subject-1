---
tip: pojam
aliases: ["uncontrolled resource consumption"]
izvor: "MITRE CWE-400: Uncontrolled Resource Consumption, https://cwe.mitre.org/data/definitions/400.html"
---

# Nekontrolisana potrošnja resursa (uncontrolled resource consumption)

## Definicija

Nekontrolisana potrošnja resursa je [[Slabost|slabost]] pri kojoj komponenta ne kontroliše obim ili trajanje korišćenja raspoloživog procesorskog vremena, memorije, prostora ili drugih kapaciteta, tako da radnje napadača mogu iscrpeti kapacitet potreban za dozvoljeno korišćenje sistema.

## Primer

Ovlašćeni korisnici treba da mogu da koriste poslovnu funkciju proizvoda. Ako jedan učesnik može bez odgovarajuće kontrole pokrenuti toliko istovremenih obrada da iscrpi memoriju i vreme izvršavanja, drugi ovlašćeni korisnici više ne mogu da koriste tu funkciju. Pretnja po komponenti je narušavanje dostupnosti obrade; konkretna ranjivost postoji ako opisane radnje u datom okruženju zaista mogu iscrpeti potrebne kapacitete. Opisani nedostatak ne zavisi od određene poslovne funkcije ili komunikacionog protokola.

## Napomene

Slabost je nekontrolisana potrošnja, dok su slanje opterećujućih zahteva radnje napada, a onemogućena usluga posledica. Sama velika potrošnja tokom dozvoljenog rada nije dovoljan dokaz ranjivosti.

Obrada, prijem podataka i upisivanje u skladište mogu trošiti različite kapacitete. Konkretne granice i zaštitni mehanizmi zavise od komponente i dozvoljenog rada, ne od jednog univerzalnog broja zahteva.
