---
tip: pojam
aliases: [Detective control]
izvor: 'Nastavna formulacija prema svrsi kontrole; izvor za primer: CIS Controls v8.1, kontrola 8 — Audit Log Management, https://www.cisecurity.org/controls/audit-log-management'
---
# Detektivna kontrola (Detective control)

## Definicija
Detektivna kontrola je bezbednosna kontrola čija je osnovna svrha da otkrije neželjeni događaj, pokušaj narušavanja bezbednosti ili njegove tragove. Omogućava da odgovorna osoba sazna za problem i pokrene proveru i odgovarajuće postupanje.

## Primer
Napadač pokušava veliki broj prijava na nalog zaposlenog.

- **Komponente:** sistem naloga i sistem za prikupljanje zapisa o radu.
- **Resurs:** evidencije prijava i podaci dostupni preko naloga.
- **Bezbednosni zahtev:** neuobičajeni pokušaji prijave moraju biti uočeni na vreme.
- **Pretnja:** pokušaj preuzimanja naloga pogađanjem pristupnih podataka.
- **Ranjivost:** neuspeli pokušaji se ne prate, pa napad ostaje neprimećen.
- **Kontrola:** beleženje neuspelih prijava i upozorenje odgovornoj osobi kada njihov broj pređe utvrđeni prag u određenom periodu.

## Napomene
- Ovo je podela **prema svrsi**. Automatsko upozorenje je [[Tehnička kontrola|tehnička kontrola]], dok je dogovoreni postupak pregleda upozorenja [[Organizaciona kontrola|organizaciona kontrola]].
- [[Evidentiranje i praćenje rada]] predstavlja važnu oblast primene detektivnih kontrola.
- Upozorenje ukazuje na potrebu za proverom; samo po sebi nije dokaz uspešnog napada.
- Detekcija ne podrazumeva automatsko blokiranje. Blokiranje može imati [[Preventivna kontrola|preventivnu]], a vraćanje ispravnog stanja [[Korektivna kontrola|korektivnu ulogu]].
- **Ideja za vizualizaciju:** događaji iz više komponenti → pregled zapisa → upozorenje.
