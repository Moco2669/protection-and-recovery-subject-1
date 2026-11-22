---
tip: pojam
aliases: [HTTP, Hypertext Transfer Protocol]
izvor: IETF RFC 9110, HTTP Semantics ([RFC](https://www.rfc-editor.org/rfc/rfc9110.html))
status: predlog
sloj: jezgro
---
# HTTP (Hypertext Transfer Protocol)

## Definicija
HTTP je [[Aplikacioni protokol|aplikacioni protokol]] za razmenu poruka između [[Klijentski program|klijentskog programa]] i [[Serverski program|serverskog programa]]; poruke predstavljaju zahteve i odgovore za resurse.

## Primer
Pregledač šalje `GET /fakture/123` serverskom programu Fakturisa. Program može vratiti `200 OK` i sadržaj stranice.

## Napomene
- [[HTTP 2|HTTP/2]] menja uokviravanje i omogućava multipleksiranje na jednoj TCP vezi; [[HTTP 3|HTTP/3]] prenosi HTTP kroz QUIC tokove.
- HTTP/1.1 i HTTP/2 se uobičajeno prenose preko [[TCP|TCP-a]], dok HTTP/3 koristi [[QUIC]] preko [[UDP]]-a.
- Osnovna semantika metoda, zaglavlja i odgovora ostaje HTTP; verzije se razlikuju po prenosu i uokviravanju.
- HTTP sam po sebi ne šifruje saobraćaj.
