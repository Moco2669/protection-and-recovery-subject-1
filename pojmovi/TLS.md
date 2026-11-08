---
tip: pojam
aliases: [Transport Layer Security, TLS protocol]
izvor: IETF RFC 8446, The Transport Layer Security (TLS) Protocol Version 1.3 ([RFC](https://www.rfc-editor.org/rfc/rfc8446.html))
status: predlog
sloj: jezgro
---
# TLS (Transport Layer Security)

## Definicija
TLS je protokol koji omogućava klijentskim i serverskim programima da komuniciraju uz zaštitu podataka od prisluškivanja, izmene i lažiranja poruka.

## Primer
Kada pregledač koristi [[HTTPS]] za pristup Fakturisu, TLS štiti razmenu [[HTTP]] podataka između pregledača i servera od čitanja i izmene tokom prenosa.

Kontraprimer: TCP sam po sebi ne šifruje podatke. Pouzdano prenosi bajtove, ali za zaštitu njihove sadržine potreban je dodatni mehanizam, kao TLS.

## Napomene
- TLS 1.3 uspostavlja bezbednosne parametre i štiti komunikaciju. U uobičajenoj kombinaciji sa HTTP/1.1 ili HTTP/2 radi preko pouzdanog prenosa kao što je TCP.
- TLS je protokol, a HTTPS je korišćenje HTTP-a uz TLS zaštitu.
