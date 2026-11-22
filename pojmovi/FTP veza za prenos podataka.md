---
tip: pojam
aliases: [FTP data connection, data connection, veza podataka, podatkovna veza]
izvor: IETF RFC 959, odeljak 3 ([RFC](https://www.rfc-editor.org/rfc/rfc959.html))
status: predlog
sloj: jezgro
---
# FTP veza za prenos podataka (FTP data connection)

## Definicija
FTP veza za prenos podataka je zasebna veza kojom se prenosi sadržaj datoteke ili listing direktorijuma, odvojeno od komandi i odgovora na [[FTP kontrolna veza|kontrolnoj vezi]].

## Primer
Komanda `RETR` ide kontrolnom vezom, bajtovi PDF-a ovom vezom, a odgovor 226 o završetku opet kontrolnom vezom.

## Napomene
- „Veza za prenos podataka“ jasnije opisuje namenu od doslovnog „podatkovna veza“.
- Klijent je inicira u [[FTP pasivni režim|pasivnom]], a server u [[FTP aktivni režim|aktivnom režimu]].

