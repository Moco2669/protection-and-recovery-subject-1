---
tip: pojam
aliases: [recursive resolver, DNS recursive resolver, DNS resolver]
izvor: IETF RFC 8499, DNS Terminology ([RFC](https://www.rfc-editor.org/rfc/rfc8499.html))
status: predlog
sloj: jezgro
---
# Rekurzivni DNS resolver (recursive DNS resolver)

## Definicija
Rekurzivni DNS resolver pribavlja odgovor u ime klijenta: proverava keš i, ako odgovora nema, šalje upite DNS hijerarhiji prateći upućivanja od [[Root DNS server|root servera]] ka serveru nadležnom za traženo ime.

## Primer
Za `www.example.com`, resolver pita root sistem za `.com`, zatim [[TLD DNS server|TLD server]] i [[Autoritativni DNS server|autoritativni server]], pa odgovor vraća klijentu.

## Napomene
- Resolver može obezbeđivati provajder, organizacija ili javni DNS operator; ne mora biti kod vlasnika domena.
- Root, TLD i autoritativni serveri daju odgovore ili upućivanja; resolver obavlja praćenje za klijenta.

