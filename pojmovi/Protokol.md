---
tip: pojam
aliases: [protocol, communication protocol, komunikacioni protokol]
izvor: IETF RFC 1392, Internet Glossary, unos protocol ([RFC](https://www.rfc-editor.org/rfc/rfc1392.html))
status: predlog
sloj: temelj
---
# Protokol (protocol)

## Definicija
U ovoj bazi, protokol je skup pravila kojima učesnici komunikacije utvrđuju kako se poruke oblikuju, šta znače i kako se razmenjuju, uključujući očekivane odgovore i postupanje pri grešci.

## Primer
Pregledač šalje [[HTTP]] zahtev [[Serverski program|serverskom programu]] Fakturisa. HTTP određuje značenje zahteva i odgovora, dok [[TCP]] određuje transportne osobine prenosa.

Kontraprimer: pravilo da zaposleni sme da odobri popust uređuje poslovno ovlašćenje, a ne razmenu poruka.

## Napomene
- „Protokol“ se šire koristi i za postupak izvan komunikacije. Ova baza koristi uži izraz „komunikacioni protokol“.
- Kriterijum podele: [[Aplikacioni protokol|aplikacioni protokol]] definiše format i značenje poruka/operacija aplikacije; [[Transportni protokol|transportni protokol]] pruža programima uslugu prenosa; [[Protokol za zaštitu komunikacije]] obezbeđuje kriptografsku zaštitu. Uloge nisu uvek isključive.
- [[HTTP]], [[DNS]], [[MQTT]] i [[FTP]] su aplikacioni; [[TCP]], [[UDP]] i [[QUIC]] transportni. [[SSH]] je porodica protokola koja objedinjuje zaštitu i udaljene usluge.
- Protokol propisuje pravila, dok je [[Tok podataka|tok podataka]] konkretan prenos u modelu sistema.
