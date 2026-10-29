---
tip: pojam
aliases: [backup system, backup, rezervna kopija]
izvor: NIST SP 800-34 Rev. 1, "backup" (https://csrc.nist.gov/glossary/term/backup)
status: predlog
sloj: temelj
---
# Sistem za rezervne kopije (backup system)

## Definicija
Sistem za rezervne kopije je [[Komponenta sistema|komponenta sistema]] koja u zadatim vremenskim razmacima pravi kopije podataka i podešavanja drugih komponenti, čuva ih i omogućava da se iz njih podaci vrate.

## Primer
Sistem za rezervne kopije firme [[Fakturis]] je poseban [[Server|server]] u server sobi. Svake noći kopira [[Baza podataka|bazu podataka]] i [[Skladište dokumenata|skladište dokumenata]], a jednom nedeljno podešavanja servera. Kopije se čuvaju 30 dana.

Kontraprimer: kada programer pre rizične izmene ručno napravi kopiju jedne tabele u istoj bazi, to jeste kopija, ali ne i sistem za rezervne kopije, jer se ne pravi redovno i deli sudbinu originala.

## Napomene
- Rezervne kopije sadrže sve što i originali, pa su i same [[Resurs|resurs]] kome treba ista zaštita poverljivosti kao originalima.
- Kopija koja nikad nije vraćena nije proverena. Firma ne zna da li može da ispuni zahtev da se podaci vrate u roku od četiri sata.
- Karakteristična ranjivost: [[Nezaštićena rezervna kopija]].
