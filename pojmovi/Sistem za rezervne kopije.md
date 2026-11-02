---
tip: pojam
aliases: [backup system]
izvor: NIST SP 800-34 Rev. 1, "backup" (https://csrc.nist.gov/glossary/term/backup)
status: predlog
sloj: temelj
---
# Sistem za rezervne kopije (backup system)

## Definicija
Sistem za rezervne kopije je komponenta sistema koja u zadatim vremenskim razmacima pravi kopije podataka i podešavanja drugih komponenti, čuva ih i omogućava da se iz njih podaci vrate.

## Primer
Sistem za rezervne kopije firme [[Fakturis]] je poseban [[Server|server]]. Svake noći kopira [[Baza podataka|bazu podataka]] i [[Skladište datoteka|skladište datoteka]], a jednom nedeljno podešavanja servera. Kopije se čuvaju 30 dana.

Kontraprimer: kada programer pre rizične izmene ručno napravi kopiju jedne tabele u istoj bazi, to jeste kopija, ali ne i sistem za rezervne kopije, jer se ne pravi redovno i deli sudbinu originala.

## Napomene
- Rezervne kopije sadrže sve što i originali, pa su i same resurs kome treba ista zaštita poverljivosti kao originalima.
- Nije [[Skladište podataka|skladište podataka]]. Iz kopija se ne radi. Podaci se iz njih vraćaju u skladište.
- Kopija koja nikad nije vraćena nije proverena.
