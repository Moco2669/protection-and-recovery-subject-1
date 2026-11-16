---
tip: pojam
aliases: [document database, document store, dokument baza, MongoDB]
izvor: nema posebne standardne definicije; karakteristike prema MongoDB Manual, Security Checklist for Self-Managed Deployments i Schema Validation
status: predlog
sloj: jezgro
---
# Dokument-orijentisana baza podataka (document database)

## Definicija
Dokument-orijentisana baza podataka je [[Baza podataka|baza podataka]] koja podatke čuva kao dokumente sa imenovanim i ugnježdenim poljima nalik JSON-u, i pronalazi ih po vrednostima tih polja.

## Primer
Kada bi [[Fakturis]] fakture čuvao u MongoDB-u, jedna faktura bila bi jedan dokument sa podacima o kupcu i listom stavki. Dve fakture u istoj kolekciji mogle bi da imaju različita polja, na primer samo jedna polje za popust.

Kontraprimer: JSON datoteka u [[Skladište datoteka|skladištu datoteka]] ima isti oblik, ali to nije dokument-orijentisana baza. Skladište ne tumači njen sadržaj i ne može da pronađe dokumente po vrednosti polja.

## Napomene
**Upotreba.** Koristi se kada dokumenti nemaju istu strukturu ili su prirodno ugnježdeni, kao katalog proizvoda ili podešavanja korisnika. Novo polje po pravilu ne traži izmenu strukture baze.

**Struktura.** Dokumenti u istoj kolekciji podrazumevano ne moraju da imaju ista polja. MongoDB ipak omogućava pravila provere šeme za kolekciju, posle kojih svaki novi dokument mora da ih zadovolji. Promenljiva struktura je zato podrazumevano ponašanje, a ne svojstvo vrste.

**Čuvanje na disku.** MongoDB čuva dokumente u binarnom obliku JSON-a (BSON), u datotekama podataka na serveru. Kao i kod [[Relaciona baza podataka|relacione baze]], ko čita te datoteke ili kopiju baze, čita sve. Te datoteke nisu dokumenti koje proizvod traži po polju.

**Pristup.** Baza prima veze na mrežnom portu, kod MongoDB-a podrazumevano 27017. Kontrolu pristupa i način prijave treba izričito uključiti. MongoDB to navodi kao prvu stavku svoje bezbednosne kontrolne liste. Posle toga i servis i čovek imaju nalog sa lozinkom, a nalog ima uloge. [[Softverski proizvod|Proizvod]] koristi [[Servisni nalog|servisni nalog]]. Administrator ima drugi nalog. Bez uključene kontrole baza ne pita ko se javlja.

**Komande.** Upit je strukturisan objekat sa operatorima, na primer `{"iznos": {"$gt": 1000}}`. Ako proizvod objekat upita sastavi od vrednosti koje šalje korisnik, korisnik umesto vrednosti može da pošalje operator i promeni značenje [[Upitni jezik|upita]]. Neke operacije, kao `$where`, izvršavaju JavaScript na serveru.

Primer je ilustrativan. Fakturis u studiji ne koristi dokument-orijentisanu bazu.
