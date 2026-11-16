---
tip: pojam
aliases: [query language, upit, query]
izvor: nema posebne standardne definicije; srodno: MITRE CWE-943, Improper Neutralization of Special Elements in Data Query Logic
status: predlog
sloj: jezgro
---
# Upitni jezik (query language)

## Definicija
Upitni jezik je jezik u kojem komponenta opisuje koje podatke [[Skladište podataka|skladište podataka]] treba da pronađe ili izmeni, a skladište taj opis tumači i izvršava.

## Primer
Da bi prikazao fakture jednog kupca, [[Softverski proizvod|softverski proizvod]] firme [[Fakturis]] šalje [[Relaciona baza podataka|bazi podataka]] SQL tekst `SELECT * FROM fakture WHERE kupac_id = 17`. Baza sama odlučuje kako da pronađe redove koji ispunjavaju uslov.

Kontraprimer: kada Jelena otvori datoteku u [[Deljeni mrežni folder|deljenom mrežnom folderu]], njen računar ne šalje upit. On traži datoteku po imenu, a skladište ne tumači njen sadržaj.

## Napomene
- Primeri su SQL kod [[Relaciona baza podataka|relacionih baza]] i upiti u obliku objekata kod [[Dokument-orijentisana baza podataka|dokument-orijentisanih baza]]. Naredbe [[Ključ-vrednost baza podataka|ključ-vrednost baze]], kao GET i SET, biraju podatak po ključu i ne opisuju koje podatke treba pronaći, pa nisu upitni jezik.
- Skladište izvršava ceo opis koji primi, u granicama prava naloga. Ono ne razlikuje deo koji je napisao programer od dela ugrađenog iz korisnikovog unosa. Na tome se zasniva grupa slabosti koju MITRE vodi kao CWE-943.
- „SQL upit“ je u bazi pretpostavljen pojam. Ova beleška ga uopštava na skladišta koja ne koriste SQL.
