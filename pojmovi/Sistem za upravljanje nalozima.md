---
tip: pojam
aliases: [identity and access management, IAM, direktorijum naloga, authentication system]
izvor: CIS Critical Security Controls v8, Glossary, "authentication systems" i "authorization systems"
status: predlog
sloj: temelj
---
# Sistem za upravljanje nalozima (identity and access management system)

## Definicija
Sistem za upravljanje nalozima je [[Komponenta sistema|komponenta sistema]] u kojoj se vode nalozi lica i procesa, proverava ko se prijavljuje i čuvaju prava pristupa dodeljena svakom nalogu.

## Primer
[[Fakturis]] ima dva takva sistema:
- centralni direktorijum naloga zaposlenih, koji održava Stefan. Istim nalogom zaposleni se prijavljuje na [[Poslovni računar|poslovni računar]], [[Skladište dokumenata|skladište dokumenata]] i GitLab, a direktorijum određuje kojim folderima i projektima sme da pristupi;
- nalozi korisnika aplikacije, koje [[Web aplikacija|web aplikacija]] vodi u [[Baza podataka|bazi podataka]], sa hešom lozinke i ulogom (korisnik ili podrška).

Kontraprimer: tabela u kojoj Stefan beleži ko je dobio koji laptop nije sistem za upravljanje nalozima, jer niko na osnovu nje ne proverava prijavu niti dodeljuje prava.

## Napomene
- Svaka druga komponenta oslanja se na ovaj sistem da bi znala ko joj šalje zahtev. Napadač koji preuzme nalog u njemu preuzima i sva prava tog naloga na svim komponentama.
- U [[Fakturis]] se na GitLab i na administratorski deo aplikacije prijavljuje samo lozinkom. Nalog programera koji je otišao i dalje je aktivan u GitLab-u.
