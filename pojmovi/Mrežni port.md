---
tip: pojam
aliases: [port, transport port, port number]
izvor: IETF RFC 9293, odeljak 3.1 ([RFC](https://www.rfc-editor.org/rfc/rfc9293.html))
status: predlog
sloj: jezgro
---
# Mrežni port (network port)

## Definicija
Mrežni port je broj u zaglavlju [[TCP]] ili [[UDP]] kojim transportni sloj razlikuje krajnje programe i prosleđuje primljene podatke odgovarajućem programu na računaru.

## Primer
Pri pristupu web usluzi, pregledač koristi izvorni TCP port, a odredišni port 80 može biti port na kojem serverski program prima HTTP saobraćaj.

## Napomene
- „Od porta do porta“ je skraćen opis transportne komunikacije. Portovi su polja transportnog protokola, iako ih aplikacije koriste za izbor usluge.
- Port nije fizički priključak niti sam identifikuje uređaj; koristi se zajedno sa mrežnom adresom i transportnim protokolom.
