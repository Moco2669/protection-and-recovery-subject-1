---
tip: pojam
aliases: [data store]
izvor: Shostack, Experiences Threat Modeling at Microsoft, 2008, tabela 1, "data store" (podatak u mirovanju)
status: predlog
sloj: temelj
---
# Skladište podataka (data store)

## Definicija
Skladište podataka je vrsta komponente sistema koja trajno čuva podatke. Druga komponenta čita ili menja podatke u konkretnoj komponenti te vrste.

## Primer
Pri izdavanju fakture [[Softverski proizvod|softverski proizvod]] firme [[Fakturis]] upisuje zapis u [[Baza podataka|bazu podataka]] i datoteku u [[Skladište datoteka|skladište datoteka]]. Ne postoji poseban sistem „skladište podataka“ sa kojim proizvod razgovara. [[Repozitorijum izvornog koda|Repozitorijum izvornog koda]] je skladište podataka u kojem stoji kod proizvoda.

Kontraprimer: [[Sistem za rezervne kopije|sistem za rezervne kopije]] drži kopije, ali iz njih niko ne radi. One služe vraćanju u neko skladište podataka.

## Napomene
- Podvrste su [[Baza podataka|baza podataka]], [[Skladište datoteka|skladište datoteka]], [[Skladište zapisa|skladište zapisa]] i [[Repozitorijum izvornog koda|repozitorijum izvornog koda]].
- [[Sistem za rezervne kopije|Sistem za rezervne kopije]] nije skladište podataka.
- Na [[Dijagram toka podataka|dijagramu toka podataka]] skladište je mesto gde se podaci čuvaju između obrada.
