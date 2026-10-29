---
tip: pojam
aliases: [weakness, tip ranjivosti]
izvor: MITRE CWE, Glossary, "weakness" (https://cwe.mitre.org/documents/glossary/)
status: predlog
sloj: temelj
---
# Slabost (weakness)

## Definicija
Slabost je nedostatak u dizajnu, implementaciji, konfiguraciji ili načinu upotrebe [[Komponenta sistema|komponente sistema]] koji, pod određenim okolnostima, može da učini komponentu [[Ranjivost|ranjivom]].

## Primer
Stari modul aplikacije [[Fakturis]] za uvoz kupaca iz XML fajla koristi XML parser koji učitava spoljne fajlove navedene u samom XML dokumentu. Modul je isključen i do njega ne vodi nijedan zahtev, pa je to slabost, ali ne i ranjivost. Kada programeri ponovo uključe uvoz na zahtev velikog korisnika, svaki korisnik može da otpremi XML koji čita fajlove sa servera. Ista slabost tada postaje ranjivost.

## Napomene
- Svaka ranjivost je pojava neke slabosti na konkretnoj komponenti, uz okolnosti koje napadaču omogućavaju da je iskoristi. Zato katalozi slabosti, kao što su CWE i OWASP Top 10, služe kao katalog tipova ranjivosti.
- Slabosti opisane u bazi: [[Neispravna kontrola pristupa]], [[Injekcija]], [[Nedovoljna provera autentičnosti podataka]], [[Nekontrolisana učestalost zahteva]], [[Ugrađeni pristupni podatak]], [[Pogrešna bezbednosna konfiguracija]], [[Nezakrpljen softver]], [[Prekomerno ovlašćenje]], [[Nedovoljno beleženje i praćenje]].
