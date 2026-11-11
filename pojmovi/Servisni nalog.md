---
tip: pojam
aliases: [service account, nalog aplikacije, tehnički nalog]
izvor: nema definicije u NIST rečniku; srodno: CIS Controls v8.1, mera 5.5 Establish and Maintain an Inventory of Service Accounts
status: predlog
sloj: jezgro
---
# Servisni nalog (service account)

## Definicija
Servisni nalog je nalog pod kojim program, a ne osoba, pristupa drugoj komponenti sistema.

## Primer
[[Softverski proizvod|Softverski proizvod]] firme [[Fakturis]] pristupa [[Relaciona baza podataka|bazi podataka]] nalogom baze koji ne pripada nijednom zaposlenom. [[Sistem za rezervne kopije|Sistem za rezervne kopije]] noću čita bazu i [[Skladište datoteka|skladište datoteka]] svojim nalogom. Oba naloga su servisni nalozi.

Kontraprimer: Stefanov administratorski nalog na serveru nije servisni nalog, iako ima više prava. Njime se prijavljuje osoba.

## Napomene
- Prava servisnog naloga određuju šta može onaj ko preuzme program koji ga koristi. Ako nalog proizvoda u bazi sme samo da čita i menja tabele proizvoda, napadač preko proizvoda ne može da obriše celu bazu. Ako je nalog administratorski, može.
- Program mora da zna lozinku ili ključ servisnog naloga u izvornom obliku. Zato se oni čuvaju u podešavanjima programa ili u [[Skladište tajni|skladištu tajni]].
- Servisnim nalogom se niko ne prijavljuje ručno, pa se njegova upotreba retko pregleda, a lozinka retko menja.
