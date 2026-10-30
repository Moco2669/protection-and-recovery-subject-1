---
tip: pojam
aliases: [Corrective control]
izvor: 'Nastavna formulacija prema svrsi kontrole; izvor za primer oporavka: CIS Controls v8.1, kontrola 11 — Data Recovery, https://www.cisecurity.org/controls/data-recovery'
---
# Korektivna kontrola (Corrective control)

## Definicija
Korektivna kontrola je bezbednosna kontrola čija je osnovna svrha da ispravi utvrđeni problem, otkloni njegove posledice ili pomogne vraćanju sistema u ispravno stanje. Može se primeniti posle otkrivanja greške, zloupotrebe ili drugog incidenta.

## Primer
Kompromitovan nalog briše poslovne dokumente iz zajedničkog skladišta. Nakon ograničavanja incidenta, firma pokreće vraćanje dokumenata.

- **Komponente:** skladište dokumenata i sistem rezervnih kopija.
- **Resurs:** poslovni dokumenti i njihove kopije.
- **Bezbednosni zahtev:** izgubljeni dokumenti moraju moći da se vrate u pouzdano stanje.
- **Pretnja:** neovlašćeno brisanje dokumenata.
- **Ranjivost:** kompromitovan nalog ima nepotrebno široka prava brisanja.
- **Kontrola:** vraćanje dokumenata iz proverene kopije, provera njihove ispravnosti i ispravka preširokih prava pre nastavka redovnog rada.

## Napomene
- Ovo je podela **prema svrsi**. [[Rezervne kopije i oporavak]] daju primer korektivnog postupanja kroz vraćanje podataka.
- Korekcija može otkloniti i slabost pre uspešnog napada: ispravka pogrešnih dozvola koriguje podešavanje i sprečava buduće zloupotrebe.
- U ovoj nastavnoj podeli oporavak obrađujemo uz korektivne kontrole. Druge podele mogu izdvajati kontrole oporavka kao posebnu kategoriju.
- [[Detektivna kontrola|Detektivna kontrola]] pomaže otkrivanju problema; [[Preventivna kontrola|preventivna]] smanjuje mogućnost ponavljanja.
- **Ideja za vizualizaciju:** problem → ograničavanje posledica → vraćanje → provera rada.
