---
tip: pojam
aliases: [transport-layer protocol, transport protocol]
izvor: IETF RFC 1122, odeljak 4 ([RFC](https://www.rfc-editor.org/rfc/rfc1122.html))
status: predlog
sloj: jezgro
---
# Transportni protokol (transport-layer protocol)

## Definicija
Transportni protokol pruža krajnjim programima pravila za prenos podataka između računara; može definisati identifikaciju programa preko [[Mrežni port|portova]], granice poruka ili toka bajtova i garancije isporuke/redosleda.

## Primer
Pregledač i [[Serverski program|serverski program]] razmenjuju [[HTTP]] preko [[TCP|TCP-a]]. HTTP daje porukama značenje, a TCP prenosi ih kao pouzdan, uređen [[Tok bajtova|tok bajtova]].

## Napomene
- Kriterijum: protokol pruža prenosnu uslugu procesima, ne značenje web, DNS ili datotečnih operacija.
- [[TCP]], [[UDP]] i [[QUIC]] su transportni protokoli sa različitim uslugama.
- Portovi su polja transportnog protokola, iako ih aplikacije koriste za izbor usluge.
- SSH-ov „transportni podprotokol“ nije isto što i TCP/UDP transportni protokol.

