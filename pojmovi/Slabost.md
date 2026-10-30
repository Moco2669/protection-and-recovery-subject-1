| **tip** | pojam |
|---|---|
| **aliases** | weakness |
| **izvor** | MITRE CWE Glossary, odrednice *Weakness* i *Vulnerability*, [https://cwe.mitre.org/documents/glossary/](https://cwe.mitre.org/documents/glossary/) |

# Slabost (weakness)

## Definicija

Slabost jeste nedostatak u softverskoj, firmverskoj, hardverskoj ili servisnoj komponenti koji pod određenim okolnostima može doprineti nastanku ranjivosti.

## Primer

U posmatranom sistemu firme, modul za pregled faktura proverava da li je korisnik prijavljen, ali ne proverava da li ima pravo da pristupi traženoj fakturi. Izostanak provere prava pristupa predstavlja slabost.

Ako korisnik promenom identifikatora u zahtevu dobije fakturu drugog preduzeća, u tom modulu postoji konkretna ranjivost: omogućeno je neovlašćeno čitanje podataka koje narušava poverljivost fakture i krši zahtev da korisnik vidi samo fakture svog preduzeća.

## Kontraprimer

Javni cenovnik firme dostupan je svakom posetiocu sajta bez prijave. Pošto je namenjen javnosti, takav pristup odgovara zahtevima firme. Odsustvo prijave u ovom slučaju nije slabost.

## Napomene

Slabost opisuje nedostatak koji može doprineti nastanku ranjivosti. Da bi se utvrdila konkretna ranjivost, potrebno je razmotriti komponentu, uslove njenog korišćenja i mogućnost da napadač iskoristi taj nedostatak za narušavanje bezbednosnog svojstva resursa.

Ista vrsta slabosti može se pojaviti u različitim komponentama i doprineti nastanku više različitih ranjivosti.

Postojanje slabosti ili ranjivosti ne znači da je napad već izveden niti da je šteta nastala.
