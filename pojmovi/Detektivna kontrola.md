---
tip: pojam
aliases: [Detective control]
izvor: 'Osnov za definiciju (parafraza): ISO/IEC 27002:2022, odeljak 4.2(a), atribut Control type, https://www.iso.org/standard/75652.html; izvor za primer: CIS Controls v8.1, kontrola 8 — Audit Log Management, https://www.cisecurity.org/controls/audit-log-management'
---
# Detektivna kontrola (Detective control)

## Definicija
Detektivna kontrola je bezbednosna kontrola čija je osnovna svrha da otkrije narušavanje bezbednosnog svojstva resursa, pokušaj narušavanja bezbednosti ili njegove tragove. Omogućava da odgovorna osoba sazna za problem i pokrene proveru i odgovarajuće postupanje.

## Primer
Napadač pokušava veliki broj prijava na nalog zaposlenog.

- **Komponente:** sistem naloga i sistem za prikupljanje zapisa o radu.
- **Resurs:** evidencije prijava i podaci dostupni preko naloga.
- **Bezbednosni zahtev:** neuobičajeni pokušaji prijave moraju biti uočeni na vreme.
- **Pretnja:** pokušaj preuzimanja naloga pogađanjem pristupnih podataka.
- **Ranjivost:** neuspeli pokušaji se ne prate, pa napad ostaje neprimećen.
- **Kontrola:** beleženje neuspelih prijava i upozorenje odgovornoj osobi kada njihov broj pređe utvrđeni prag u određenom periodu.

## Napomene
- ISO/IEC 27002:2022, odeljak 4.2(a), detektivno dejstvo vezuje za delovanje pri nastanku incidenta. Definicija je parafraza sa dodatnim objašnjenjem otkrivanja pokušaja i tragova, a ne doslovan prevod standarda.
- Ovo je podela **prema svrsi**. Automatsko upozorenje je [[Tehnička kontrola|tehnička kontrola]], dok je dogovoreni postupak pregleda upozorenja [[Organizaciona kontrola|organizaciona kontrola]].
- [[Sistem za zapise o radu]] je komponenta koja prikupljanjem, čuvanjem i omogućavanjem pregleda zapisa podržava sprovođenje detektivnih kontrola.
- Upozorenje ukazuje na potrebu za proverom; samo po sebi nije dokaz uspešnog napada.
- Detekcija ne podrazumeva automatsko blokiranje. Blokiranje može imati [[Preventivna kontrola|preventivnu]], a vraćanje ispravnog stanja [[Korektivna kontrola|korektivnu ulogu]].
- **Ideja za vizualizaciju:** događaji iz više komponenti → pregled zapisa → upozorenje.
