---
tip: pojam
aliases: [QUIC, Quick UDP Internet Connections, QUIC transport protocol]
izvor: IETF RFC 9000 ([RFC](https://www.rfc-editor.org/rfc/rfc9000.html))
status: predlog
sloj: jezgro
---
# QUIC (QUIC transport protocol)

## Definicija
QUIC je transportni protokol preko UDP datagrama koji dodaje pouzdane tokove, kontrolu zagušenja, upravljanje vezom i kriptografsku zaštitu.

## Primer
[[HTTP 3|HTTP/3]] koristi QUIC tok za svaki zahtev/odgovor. Gubitak podataka na jednom toku ne zaustavlja po redosledu sve ostale tokove kao zajednički TCP tok.

## Napomene
- QUIC nije spoj TCP-a i UDP-a: koristi UDP kao datagramski prenos, a sam implementira potrebne transportne funkcije.
- Klasifikuje se kao transportni protokol, iako pruža i kriptografski handshake i šifrovanje.
- UDP sam ne obezbeđuje pouzdanost, redosled, tokove ni zaštitu.
