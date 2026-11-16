---
tip: pojam
aliases: [authoritative DNS server, authoritative name server]
izvor: IETF RFC 1034, Domain Names — Concepts and Facilities ([RFC](https://www.rfc-editor.org/rfc/rfc1034.html))
status: predlog
sloj: jezgro
---
# Autoritativni DNS server (authoritative DNS server)

## Definicija
Autoritativni DNS server je serverski program koji daje odgovore iz podataka DNS zone za koju je nadležan.

## Primer
Autoritativni server za `example.com` čuva zapise za `www.example.com`; na upit A vraća IPv4 zapis, a na AAAA IPv6 zapis.

## Napomene
- Odgovor potiče iz podataka zone kojima je server nadležan, za razliku od keširanog odgovora resolvera.
- Može biti hostovan kod DNS operatora ili u infrastrukturi vlasnika domena. Root/TLD serveri su autoritativni za svoje zone, ali nisu autoritativni serveri konkretnog sajta.

