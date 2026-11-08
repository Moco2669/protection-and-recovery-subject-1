---
tip: pojam
aliases: [application-layer protocol, application protocol]
izvor: IETF RFC 9110, HTTP Semantics, odeljci 1 i 4.2 ([RFC](https://www.rfc-editor.org/rfc/rfc9110.html))
status: predlog
sloj: jezgro
---
# Aplikacioni protokol (application-layer protocol)

## Definicija
Aplikacioni protokol je [[Protokol|protokol]] koji određuje značenje, oblik i razmenu poruka kojima programi ostvaruju određenu funkciju.

## Primer
Kada korisnik u pregledaču pošalje zahtev za izdavanje fakture, [[HTTP]] definiše kako [[Softverski proizvod|softverski proizvod]] firme [[Fakturis]] razume zahtev i oblikuje odgovor. HTTP je aplikacioni protokol zato što uređuje razmenu između programa, nezavisno od toga kako je prenos nižim slojevima ostvaren.

Kontraprimer: [[TCP]] ne određuje šta znači zahtev za izdavanje fakture. On je [[Transportni protokol|transportni protokol]] koji prenosi podatke potrebne za komunikaciju.

## Napomene
- Primeri aplikacionih protokola su [[HTTP]], [[DNS]], [[SSH]] i [[MQTT]]. [[HTTPS]] označava HTTP komunikaciju zaštićenu [[TLS|TLS-om]].
- „Aplikacioni“ opisuje ulogu protokola, a ne nužno mesto gde se izvršava. Protokol koriste programi na krajnjim sistemima.
