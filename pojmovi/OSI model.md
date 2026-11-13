---
tip: pojam
aliases: [OSI model, Open Systems Interconnection model]
izvor: ITU-T Recommendation X.200 ([ITU](https://www.itu.int/rec/T-REC-X.200/en))
status: predlog
sloj: jezgro
---
# OSI model (OSI reference model)

## Definicija
OSI model je referentni model koji komunikacione funkcije organizuje u sedam slojeva, od fizičkog prenosa signala do aplikacijskih usluga.

## Primer
Pristup Fakturisu preko HTTP-a može se okvirno posmatrati kroz HTTP razmenu, TCP prenos, IP rutiranje, lokalnu vezu i fizički signal. Ne znači da se svaki protokol uklapa u tačno jedan sloj.

## Napomene
1. **Fizički** — prenos signala; npr. optika/Ethernet fizički sloj.
2. **Veza podataka** — lokalni okviri; npr. Ethernet, Wi‑Fi MAC.
3. **Mrežni** — adresiranje/rutiranje; npr. IP.
4. **Transportni** — komunikacija programa; npr. [[TCP]], [[UDP]], [[QUIC]].
5. **Sesijski** — upravljanje dijalogom/sesijom; često funkcije ostalih slojeva.
6. **Prezentacioni** — kodiranje, kompresija ili transformacija podataka.
7. **Aplikacioni** — usluge/protokoli aplikacija; npr. [[HTTP]], [[DNS]], [[FTP]], [[MQTT]], [[SSH]].

Osim aplikacionih i transportnih, po OSI slojevima postoje i protokoli mrežnog sloja, sloja veze podataka, sesijskog sloja, prezentacionog sloja i fizičkog sloja. Protokoli za zaštitu komunikacije predstavljaju funkcionalnu kategoriju, ne dodatni OSI sloj.

Pregled služi za orijentaciju, ne za strogo svrstavanje. [[Protokol za zaštitu komunikacije]] i SSH imaju funkcije koje prelaze jednostavno mapiranje slojeva. [[TCP IP model|TCP/IP model]] koristi manje slojeva.
