---
tip: pojam
aliases: [Hypertext Transfer Protocol]
izvor: IETF RFC 9110, HTTP Semantics, odeljak 1 ([RFC](https://www.rfc-editor.org/rfc/rfc9110.html))
status: predlog
sloj: jezgro
---
# HTTP (Hypertext Transfer Protocol)

## Definicija
HTTP je [[Aplikacioni protokol|aplikacioni protokol]] koji uređuje zahteve i odgovore kojima klijent i server razmenjuju podatke o resursima.

## Primer
Ako pregledač korisnika koristi HTTP da zatraži stranicu za izdavanje fakture, [[Softverski proizvod|softverski proizvod]] firme [[Fakturis]] prima zahtev i vraća odgovor, na primer stranicu sa poljima za unos stavki.

Kontraprimer: TCP ne određuje šta znači zahtev za stranicu fakture. On prenosi bajtove između računara, dok HTTP određuje značenje i oblik zahteva i odgovora.

## Napomene
- HTTP/1.1 i HTTP/2 se često koriste preko [[TCP|TCP-a]].
- HTTP sam po sebi ne šifruje razmenjene podatke. Za HTTP komunikaciju zaštićenu TLS-om koristi se [[HTTPS]].
