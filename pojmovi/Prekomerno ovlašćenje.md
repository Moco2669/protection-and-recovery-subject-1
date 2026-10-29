---
tip: pojam
aliases: [excessive privilege, unnecessary privileges, prekomerna ovlašćenja, prekomerna prava pristupa]
izvor: CWE-250 Execution with Unnecessary Privileges; CWE-269 Improper Privilege Management; NIST SP 800-53 Rev. 5, AC-6 Least Privilege
status: predlog
sloj: jezgro
---
# Prekomerno ovlašćenje (excessive privilege)

## Definicija
Prekomerno ovlašćenje je [[Ranjivost|ranjivost]] [[Komponenta sistema|komponente sistema]] u kojoj lice, nalog ili proces ima veća prava pristupa nego što su mu potrebna za njegov zadatak.

## Primer
Prekomerna ovlašćenja u firmi [[Fakturis]], po komponentama:
- [[Baza podataka]]: aplikacija se povezuje kao vlasnik baze, pa SQL injekcija u pretrazi kupaca ne samo da čita tuđe kupce, nego može da obriše sve tabele;
- [[Skladište dokumenata]]: svi zaposleni imaju pravo čitanja i pisanja nad celim deljenim folderom, uključujući finansijske izveštaje. Ransomware pokrenut sa bilo kog laptopa može da šifruje sve dokumente;
- [[Poslovni računar]]: zaposleni rade kao lokalni administratori, pa makro iz priloga e-pošte može da instalira program;
- [[Sistem za upravljanje nalozima]]: nalog programera koji je otišao pre dva meseca i dalje je aktivan u GitLab-u;
- veza sa PayNet-om u [[Web aplikacija|web aplikaciji]]: API ključ ima i pravo povraćaja novca, iako aplikacija samo naplaćuje;
- testno okruženje uz [[Repozitorijum izvornog koda|repozitorijum]] koristi kopiju produkcione baze, pa programeri koji testiraju vide prave podatke korisnika.

## Napomene
- Ova ranjivost često ne omogućava prvi korak napada, ali određuje koliko štete napadač može da načini posle njega. U [[Napad|napadu]] ransomware grupe administratorska prava su ono što makrou omogućava da instalira program.
- Suprotni princip je princip najmanjih privilegija (least privilege): svako dobija samo prava potrebna za svoj zadatak.
