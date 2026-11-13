---
tip: pojam
aliases: [FTP passive mode, passive FTP]
izvor: IETF RFC 959, odeljak 3.2 ([RFC](https://www.rfc-editor.org/rfc/rfc959.html)); RFC 2428 ([RFC](https://www.rfc-editor.org/rfc/rfc2428.html))
status: predlog
sloj: jezgro
---
# FTP pasivni režim (FTP passive mode)

## Definicija
FTP pasivni režim je način rada u kojem klijent zatraži pasivni endpoint, server saopšti port na kojem sluša, a klijent inicira [[FTP veza za prenos podataka|vezu za prenos podataka]] ka serveru.

## Primer
Klijent šalje `EPSV`; server vraća `229 Entering Extended Passive Mode (|||50000|)`. Klijent otvara drugu TCP vezu ka portu 50000 na istom serveru.

## Napomene
- Režim se često lakše koristi iza [[Prevođenje mrežnih adresa|NAT-a]] jer klijent inicira obe veze; serverova mreža ipak mora dozvoliti pasivni opseg portova.
- EPSV vraća samo port i klijent koristi adresu servera sa kontrolne veze. PASV odgovor 227 može sadržati adresu i port.


