---
tip: pojam
aliases: [document database, document store, dokument baza, NoSQL baza, MongoDB]
izvor: nema posebne standardne definicije; karakteristike prema MongoDB Manual, Security Checklist for Self-Managed Deployments
status: predlog
sloj: jezgro
---
# Dokument-orijentisana baza podataka (document database)

## Definicija
Dokument-orijentisana baza podataka je [[Baza podataka|baza podataka]] koja podatke čuva kao dokumente, zapise sa imenovanim i ugnježdenim poljima nalik JSON-u, bez strukture koju svi dokumenti moraju da prate.

## Primer
Kada bi [[Fakturis]] fakture čuvao u MongoDB-u, jedna faktura bila bi jedan dokument sa podacima o kupcu i listom stavki. Dve fakture u istoj kolekciji mogle bi da imaju različita polja, na primer samo jedna polje za popust.

Kontraprimer: JSON datoteka u [[Skladište datoteka|skladištu datoteka]] ima isti oblik, ali to nije dokument-orijentisana baza. Skladište ne tumači njen sadržaj i ne može da pronađe dokumente po vrednosti polja.

## Napomene
**Upotreba.** Koristi se kada zapisi nemaju istu strukturu ili su prirodno ugnježdeni, kao katalog proizvoda ili podešavanja korisnika. Novo polje ne traži izmenu strukture baze.

**Čuvanje na disku.** MongoDB čuva dokumente u binarnom zapisu JSON-a (BSON), u datotekama podataka na serveru. Kao i kod [[Relaciona baza podataka|relacione baze]], ko čita te datoteke ili kopiju baze, čita sve.

**Pristup.** Baza prima veze na mrežnom portu, kod MongoDB-a podrazumevano 27017. Kontrolu pristupa i način prijave treba izričito uključiti; MongoDB to navodi kao prvu stavku svoje bezbednosne kontrolne liste. Posle prijave nalog ima prava svojih uloga.

**Komande.** Upit je strukturisan objekat sa operatorima, na primer `{"iznos": {"$gt": 1000}}`. Ako proizvod objekat upita sastavi od vrednosti koje šalje korisnik, korisnik umesto vrednosti može da pošalje operator i promeni značenje [[Upitni jezik|upita]]. Neke operacije, kao `$where`, izvršavaju JavaScript na serveru.

Primer je ilustrativan. Fakturis u studiji ne koristi dokument-orijentisanu bazu.
