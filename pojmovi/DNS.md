---
tip: pojam
aliases: [DNS, Domain Name System]
izvor: IETF RFC 1034, Domain Names — Concepts and Facilities ([RFC](https://www.rfc-editor.org/rfc/rfc1034.html)); RFC 1035 ([RFC](https://www.rfc-editor.org/rfc/rfc1035.html))
status: predlog
sloj: jezgro
---
# DNS (Domain Name System)

## Definicija
DNS je distribuirani sistem imenovanja i [[Aplikacioni protokol|aplikacioni protokol]] kojim klijenti traže podatke povezane sa imenima domena, a DNS serveri vraćaju odgovore ili upućivanja.

## Primer
Stub resolver korisnikovog uređaja traži `www.example.com`. [[Rekurzivni DNS resolver|Rekurzivni resolver]] može pitati [[Root DNS server|root]], [[TLD DNS server|TLD]] pa [[Autoritativni DNS server|autoritativni server]]; autoritativni odgovor može sadržati [[DNS zapis|A zapis]] za IPv4 ili AAAA za IPv6.

## Napomene
- [[Poddomen|Poddomen]] je ime ispod nadređenog domena, npr. `shop.example.com`.
- Root serveri su globalna distribuirana infrastruktura sa 13 logičkih identiteta i mnogo fizičkih instanci; nisu serveri unutar organizacije koja traži domen.
- Rekurzivni resolver može biti kod provajdera, organizacije ili javnog DNS operatora. Autoritativni DNS server može biti kod vlasnika domena ili njegovog DNS hosting provajdera.
- Pitanje i odgovorni odeljci opisani su u [[DNS poruka|DNS poruci]]. DNS najčešće koristi [[UDP]], ali koristi i [[TCP]] kada je potrebno, npr. za veće odgovore i prenos zona. Nije svaki DNS server „u okviru iste organizacije“.


