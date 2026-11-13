---
tip: pojam
aliases: [application-layer protocol, application protocol]
izvor: IETF RFC 1123 ([RFC](https://www.rfc-editor.org/rfc/rfc1123.html)); IETF RFC 9110, odeljak 1 ([RFC](https://www.rfc-editor.org/rfc/rfc9110.html))
status: predlog
sloj: jezgro
---
# Aplikacioni protokol (application-layer protocol)

## Definicija
Aplikacioni protokol je [[Protokol|komunikacioni protokol]] čije poruke predstavljaju operacije i podatke aplikacije, na primer web zahtev, DNS pitanje, komandu za prenos datoteke ili MQTT objavu; definiše strukturu i značenje tih poruka, ne opštu uslugu prenosa između programa.

## Primer
[[HTTP]] definiše metod, putanju, zaglavlja i značenje odgovora kada korisnik zatraži stranicu Fakturisa. [[TCP]] ili [[QUIC]] mogu preneti HTTP poruke, ali ne određuju šta znači zahtev za fakturu.

## Napomene
- Praktičan kriterijum: ako protokol određuje aplikacijske operacije i značenje poruka, klasifikujemo ga kao aplikacioni. To opisuje ulogu, ne mesto izvršavanja ili vidljivost korisniku.
- Primeri: [[HTTP]], [[DNS]], [[FTP]], [[MQTT]]. [[SSH]] je porodica protokola za udaljene usluge sa komponentama za zaštitu, prijavu i kanale.
- [[Protokol za zaštitu komunikacije]] se svrstava prema zaštitnoj ulozi, ne nasilno u aplikacione ili TCP/UDP protokole.
- RFC 9110 opisuje HTTP; ne definiše univerzalnu klasu aplikacionih protokola.
