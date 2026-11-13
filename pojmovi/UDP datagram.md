---
tip: pojam
aliases: [UDP datagram, UDP packet]
izvor: IETF RFC 768, User Datagram Protocol ([RFC](https://www.rfc-editor.org/rfc/rfc768.html))
status: predlog
sloj: jezgro
---
# UDP datagram (UDP datagram)

## Definicija
UDP datagram je samostalna poruka UDP-a sa zaglavljem i sadržajem; UDP prenosi granicu datagrama do prijemnog programa, ali sam ne garantuje isporuku ni redosled.

## Primer
Aplikacija glasovnog poziva podeli zvuk na kratke komade i svaki šalje kao UDP datagram. Ako se jedan izgubi ili zakasni, aplikacija može nastaviti sa narednim.

## Napomene
- Za razliku od [[Tok bajtova|TCP toka bajtova]], UDP čuva granicu poruke: jedan poslati datagram odgovara jednoj primljenoj poruci ako stigne.
- Datagram može biti izgubljen, dupliran ili stići van redosleda; UDP sam ne potvrđuje prijem.
- UDP datagram se prenosi u IP paketu; nazivi datagram i paket ne moraju označavati istu mrežnu jedinicu.

