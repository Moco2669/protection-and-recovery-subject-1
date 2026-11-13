---
tip: pojam
aliases: [FTP active mode, active FTP]
izvor: IETF RFC 959, odeljak 3.2 ([RFC](https://www.rfc-editor.org/rfc/rfc959.html)); RFC 2428 ([RFC](https://www.rfc-editor.org/rfc/rfc2428.html))
status: predlog
sloj: jezgro
---
# FTP aktivni režim (FTP active mode)

## Definicija
FTP aktivni režim je način rada u kojem klijent saopšti adresu i port na kojem čeka, a server inicira [[FTP veza za prenos podataka|vezu za prenos podataka]] ka klijentu.

## Primer
Klijent šalje `EPRT |1|198.51.100.25|49152|`; server potom otvara TCP vezu ka toj adresi i portu.

## Napomene
- Odlaznu vezu servera može blokirati [[Prevođenje mrežnih adresa|NAT]] ili firewall klijenta.
- Zloupotreba PORT/EPRT da server kontaktira treći host/port je FTP bounce. Ograničiti odredišta i onemogućiti neophodni proxy FTP.
- EPRT proširuje PORT za IPv4/IPv6.


