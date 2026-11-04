---
tip: pojam
aliases: [Corrective control]
izvor: 'Osnov za definiciju (parafraza): ISO/IEC 27002:2022, odeljak 4.2(a), atribut Control type, https://www.iso.org/standard/75652.html; izvor za primer oporavka: CIS Controls v8.1, kontrola 11 — Data Recovery, https://www.cisecurity.org/controls/data-recovery'
---
# Korektivna kontrola (Corrective control)

## Definicija
Korektivna kontrola je bezbednosna kontrola čija je osnovna svrha da ispravi utvrđeni problem, otkloni njegove posledice ili pomogne vraćanju sistema u ispravno stanje. Deluje nakon nastanka bezbednosnog incidenta radi otklanjanja posledica i vraćanja pouzdanog stanja.

## Primer
Kompromitovan nalog briše poslovne dokumente iz zajedničkog skladišta. Nakon ograničavanja incidenta, firma pokreće vraćanje dokumenata.

- **Komponente:** skladište dokumenata i sistem rezervnih kopija.
- **Resurs:** poslovni dokumenti i njihove kopije.
- **Bezbednosni zahtev:** izgubljeni dokumenti moraju moći da se vrate u pouzdano stanje.
- **Pretnja:** neovlašćeno brisanje dokumenata.
- **Ranjivost:** kompromitovan nalog ima nepotrebno široka prava brisanja.
- **Kontrola:** vraćanje dokumenata iz proverene kopije, provera njihove ispravnosti i ispravka preširokih prava pre nastavka redovnog rada.

## Napomene
- ISO/IEC 27002:2022, odeljak 4.2(a), korektivno dejstvo vezuje za delovanje nakon nastanka incidenta. Definicija je parafraza sa objašnjenjem ispravljanja posledica i oporavka, a ne doslovan prevod standarda.
- Ovo je podela **prema svrsi**. [[Sistem za rezervne kopije]] je komponenta koja omogućava sprovođenje korektivne kontrole vraćanjem podataka iz proverene kopije.
- Ispravka pogrešnih dozvola pre incidenta ima preventivnu svrhu u odnosu na moguću zloupotrebu. Sama činjenica da mera nešto ispravlja ne određuje njeno dejstvo u odnosu na incident.
- U ovoj nastavnoj podeli oporavak obrađujemo uz korektivne kontrole. Druge podele mogu izdvajati kontrole oporavka kao posebnu kategoriju.
- [[Detektivna kontrola|Detektivna kontrola]] pomaže otkrivanju problema; [[Preventivna kontrola|preventivna]] smanjuje mogućnost ponavljanja.
- **Ideja za vizualizaciju:** problem → ograničavanje posledica → vraćanje → provera rada.
