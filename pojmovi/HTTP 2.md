---
tip: pojam
aliases: [HTTP/2, HTTP2, Hypertext Transfer Protocol version 2]
izvor: IETF RFC 9113, HTTP/2 ([RFC](https://www.rfc-editor.org/rfc/rfc9113.html))
status: predlog
sloj: jezgro
---
# HTTP/2 (HTTP version 2)

## Definicija
HTTP/2 je verzija [[HTTP]] protokola koja zadržava semantiku HTTP zahteva i odgovora, ali ih kodira u binarne frejmove i omogućava više logičkih tokova na jednoj transportnoj vezi.

## Primer
Pregledač paralelno traži HTML, stil i slike sa Fakturisa. HTTP/2 raspoređuje frejmove tih razmena u zasebne HTTP tokove preko jedne [[TCP]] veze.

## Napomene
- Prednosti u odnosu na tipičan HTTP/1.1: multipleksiranje zahteva, kompresija zaglavlja HPACK i manje potrebe za mnogim TCP vezama.
- HTTP/2 ne uklanja TCP blokiranje po redu: ako segment nedostaje, TCP čeka ponovno slanje pre isporuke narednih bajtova aplikaciji; zato mogu čekati frejmovi svih HTTP/2 tokova na toj vezi.
- Zahtevi i odgovori ostaju HTTP poruke; menja se uokviravanje i raspoređivanje, ne osnovno značenje.
- HTTP/2 se tipično prenosi preko TCP veze.
