---
tip: pojam
aliases: [HTTP/3, HTTP3, Hypertext Transfer Protocol version 3]
izvor: IETF RFC 9114 ([RFC](https://www.rfc-editor.org/rfc/rfc9114.html)); RFC 9000 ([RFC](https://www.rfc-editor.org/rfc/rfc9000.html))
status: predlog
sloj: jezgro
---
# HTTP/3 (HTTP version 3)

## Definicija
HTTP/3 je verzija [[HTTP]] protokola čije se poruke prenose kroz tokove [[QUIC]] protokola, koji radi preko [[UDP]]-a i obezbeđuje pouzdan, uređen prenos unutar svakog toka, zaštitu i multipleksiranje.

## Primer
Pregledač traži HTML i sliku. HTTP/3 koristi odvojen QUIC tok za svaku razmenu. Gubitak paketa za sliku ne nameće čekanje zbog zajedničkog TCP redosleda pre nego što se podaci drugog toka isporuče.

## Napomene
- HTTP/3 čuva osnovnu semantiku HTTP zahteva/odgovora, ali uokviravanje i tokove oslanja na QUIC. Nije HTTP/1.1 samo prebačen na UDP.
- UDP sam ne daje pouzdanost, redosled, tokove ili zaštitu; te funkcije obezbeđuje QUIC, koji uspostavlja kriptografske ključeve i štiti pakete.
- HTTP/3 ne koristi TCP. Unutar svakog toka redosled se čuva; zajednička kontrola zagušenja može ipak ograničiti celu vezu.
