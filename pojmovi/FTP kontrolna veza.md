---
tip: pojam
aliases: [FTP control connection, FTP control channel]
izvor: IETF RFC 959, odeljak 5 ([RFC](https://www.rfc-editor.org/rfc/rfc959.html))
status: predlog
sloj: jezgro
---
# FTP kontrolna veza (FTP control connection)

## Definicija
FTP kontrolna veza je TCP veza klijenta i servera kojom se razmenjuju FTP komande i tekstualni odgovori.

## Primer
Klijent šalje `USER ana`, `PASS letmein2026`, `EPSV` i `RETR izvestaj.pdf`; odgovori 331, 230, 229 i 150 vraćaju se tom vezom.

## Napomene
- Lozinka je demonstraciona; običan FTP je šalje nešifrovano. Za poverljive prenose ne koristiti običan FTP.
- Veza obično ide ka TCP portu 21 i ostaje otvorena tokom sesije.



