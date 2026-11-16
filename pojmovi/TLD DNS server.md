---
tip: pojam
aliases: [TLD DNS server, top-level domain server, TLD name server]
izvor: IETF RFC 1034 ([RFC](https://www.rfc-editor.org/rfc/rfc1034.html))
status: predlog
sloj: jezgro
---
# TLD DNS server (TLD DNS server)

## Definicija
TLD DNS server je autoritativni DNS server za zonu vršnog domena, kao `.com` ili `.rs`, koji resolveru daje upućivanje ka autoritativnim serverima domena ispod tog vršnog domena.

## Primer
Za `www.example.com`, `.com` server upućuje resolver ka autoritativnim serverima za `example.com`; ne mora znati konačnu adresu sajta.

## Napomene
- TLD server je deo DNS hijerarhije, ne nužno infrastruktura organizacije koja koristi domen.
- Vlasnik domena obično angažuje DNS operatora koji održava autoritativne servere za svoju zonu.

