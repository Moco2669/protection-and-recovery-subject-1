---
tip: pojam
aliases: [TCP/IP model, Internet protocol suite layers]
izvor: IETF RFC 1122 ([RFC](https://www.rfc-editor.org/rfc/rfc1122.html))
status: predlog
sloj: jezgro
---
# TCP/IP model (TCP/IP model)

## Definicija
TCP/IP model je slojeviti prikaz internet komunikacije zasnovan na Internet skupu protokola; uobičajeno razlikuje aplikacioni, transportni, internet i sloj pristupa mreži.

## Primer
HTTP poruka može biti sadržaj TCP segmenta; segment se prenosi u IP paketu, a paket okviru lokalne mreže. Svaki sloj koristi uslugu sloja ispod sebe.

## Napomene
- Aplikacioni: [[HTTP]], [[DNS]], [[FTP]], [[MQTT]], [[SSH]]. Transportni: [[TCP]], [[UDP]], [[QUIC]]. Internet: IP. Pristup mreži: Ethernet/Wi‑Fi.
- [[OSI model]] ima sedam referentnih slojeva; TCP/IP model obično četiri. Preslikavanje je približno.

