---
tip: pojam
aliases: [excessive privilege, unnecessary privileges, prekomerna ovlašćenja, prekomerna prava pristupa]
izvor: CWE-250 Execution with Unnecessary Privileges; CWE-269 Improper Privilege Management; NIST SP 800-53 Rev. 5, AC-6 Least Privilege
status: predlog
sloj: jezgro
---
# Prekomerno ovlašćenje (excessive privilege)

## Definicija
Prekomerno ovlašćenje je [[Slabost|slabost]] u kojoj lice, nalog ili proces u okviru [[Komponenta sistema|komponente sistema]] ima veća prava pristupa nego što su mu potrebna za njegov zadatak.

## Primer
Prekomerna ovlašćenja u firmi [[Fakturis]]:
- aplikacija se povezuje na bazu kao njen vlasnik, pa SQL injekcija u pretrazi kupaca ne samo da čita tuđe kupce, nego može da obriše sve tabele;
- zaposleni rade na laptopovima kao lokalni administratori, pa makro iz priloga e-pošte može da instalira program;
- API ključ za PayNet ima i pravo povraćaja novca, iako aplikacija samo naplaćuje;
- nalog programera koji je otišao pre dva meseca i dalje je aktivan u GitLab-u;
- testno okruženje koristi kopiju produkcione baze, pa programeri koji testiraju vide prave podatke korisnika.

## Napomene
- Ova slabost često ne omogućava prvi korak napada, ali određuje koliko štete napadač može da načini posle njega. U [[Napad|napadu]] ransomware grupe administratorska prava su ono što makrou omogućava da instalira program.
- Suprotni princip je princip najmanjih privilegija (least privilege): svako dobija samo prava potrebna za svoj zadatak.
