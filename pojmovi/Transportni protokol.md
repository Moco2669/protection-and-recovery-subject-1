---
tip: pojam
aliases: [transport-layer protocol, transport protocol]
izvor: IETF RFC 1122, odeljak 4, "Transport Layer" ([RFC](https://www.rfc-editor.org/rfc/rfc1122.html))
status: predlog
sloj: jezgro
---
# Transportni protokol (transport-layer protocol)

## Definicija
Transportni protokol je [[Protokol|protokol]] koji krajnjim programima na umreženim računarima pruža pravila za prenos njihovih podataka između tih računara.

## Primer
Ako pregledač korisnika i [[Softverski proizvod|softverski proizvod]] firme [[Fakturis]] razmenjuju [[HTTP]] poruke preko [[TCP|TCP-a]], HTTP određuje značenje zahteva i odgovora, dok TCP prenosi njihov sadržaj između računara i obezbeđuje pouzdan, uređen tok bajtova.

Kontraprimer: [[HTTP]] nije transportni protokol. On uređuje aplikacionu razmenu, a [[TCP]] i [[UDP]] su primeri transportnih protokola.

## Napomene
- Primeri transportnih protokola su [[TCP]] i [[UDP]]. TCP obezbeđuje pouzdan i uređen tok bajtova; UDP sam ne garantuje isporuku ni redosled.
- Primer sa HTTP-om i TCP-om ilustruje jednu kombinaciju protokola, a ne jedinu moguću. Konkretan protokol prenosa Fakturisovog proizvoda nije utvrđen u studiji slučaja.
