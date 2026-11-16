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
Pri izdavanju fakture [[Softverski proizvod|softverski proizvod]] firme [[Fakturis]] upisuje red u [[Baza podataka|bazu podataka]] i datoteku u [[Skladište datoteka|skladište datoteka]]. Ne postoji poseban sistem „skladište podataka“ sa kojim proizvod razgovara. [[Repozitorijum izvornog koda|Repozitorijum izvornog koda]] je skladište podataka u kojem stoji kod proizvoda.

Kontraprimer: [[Sistem za rezervne kopije|sistem za rezervne kopije]] drži kopije, ali iz njih niko ne radi. One služe vraćanju u neko skladište podataka.

## Napomene
- Podvrste su [[Baza podataka|baza podataka]], [[Skladište datoteka|skladište datoteka]], [[Skladište zapisa|skladište zapisa]] i [[Repozitorijum izvornog koda|repozitorijum izvornog koda]]. [[Skladište tajni|Skladište tajni]] nije peta podvrsta: isti oblik, naziv i vrednost, ima i [[Ključ-vrednost baza podataka|ključ-vrednost baza]], a razlikuju se zaštite.
- Datoteka je imenovani niz bajtova. [[Skladište datoteka|Skladište datoteka]] njen sadržaj ne tumači. PDF, slika i JSON datoteka na deljenom folderu zato stoje u istom skladištu. Skladište među njima ne pravi razliku.
- Podatak koji baza čuva skladište adresira po strukturi. U [[Relaciona baza podataka|relacionoj bazi]] to je red i kolona, u [[Dokument-orijentisana baza podataka|dokument-orijentisanoj bazi]] dokument i polje, u [[Ključ-vrednost baza podataka|ključ-vrednost bazi]] ključ i vrednost. Ta vrednost je broj, tekst ili lista, a ne datoteka.
- JSON dokument u dokument-orijentisanoj bazi nije datoteka, iako na disku servera stoji u datoteci baze. Skladište ga nalazi po vrednosti polja. Ista sadržina kao JSON datoteka na deljenom folderu jeste datoteka, i po polju se ne može tražiti.
- [[Sistem za rezervne kopije|Sistem za rezervne kopije]] nije skladište podataka.
- Kako se servis ili čovek predstavlja skladištu zavisi od podvrste. To piše u odeljku Pristup njene beleške. Pristupni token je vrednost koja se pokazuje umesto lozinke.
