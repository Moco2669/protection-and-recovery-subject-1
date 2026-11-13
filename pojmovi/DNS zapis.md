---
tip: pojam
aliases: [DNS record, resource record, DNS resource record]
izvor: IETF RFC 1035, odeljak 3.2 ([RFC](https://www.rfc-editor.org/rfc/rfc1035.html)); RFC 3596 ([RFC](https://www.rfc-editor.org/rfc/rfc3596.html))
status: predlog
sloj: jezgro
---
# DNS zapis (DNS resource record)

## Definicija
DNS zapis je stavka DNS zone koja povezuje ime domena sa vrednošću određenog tipa, na primer IP adresom, aliasom ili podacima o poštanskom serveru.

## Primer
Zona može sadržati `www.example.com A 203.0.113.10` i `www.example.com AAAA 2001:db8::10`. Prvi zapis daje IPv4, drugi IPv6 adresu.

## Napomene
- A mapira ime na IPv4 adresu (32 bita); AAAA mapira ime na IPv6 adresu (128 bita). To su različiti tipovi DNS zapisa.
- Za isto ime može biti više zapisa/adresa.
- Autoritativni server čuva zapise zone; [[Rekurzivni DNS resolver|resolver]] ih može privremeno keširati prema TTL-u.

