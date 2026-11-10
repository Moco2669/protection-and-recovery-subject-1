---
tip: pojam
aliases: [protocol, communication protocol]
izvor: IETF RFC 1392, Internet Glossary, unos "protocol" ([RFC](https://www.rfc-editor.org/rfc/rfc1392.html))
status: predlog
sloj: temelj
---
# Protokol (protocol)

## Definicija
Protokol je skup pravila i formata poruka kojih se dva ili više učesnika pridržavaju da bi razmenili podatke.

## Primer
Kada korisnik koristi [[Softverski proizvod|softverski proizvod]] firme [[Fakturis]], [[HTTP]] određuje oblik zahteva koje proizvod prima i odgovora koje vraća. Ako se prenos obavlja preko [[HTTPS|HTTPS-a]], razmena HTTP podataka zaštićena je protokolom [[TLS]].

Kontraprimer: pravila koja određuju ko u Fakturisu sme da izda fakturu nisu komunikacioni protokol. Ona uređuju prava pristupa, a ne format i razmenu poruka.

## Napomene
- Protokol opisuje pravila razmene, dok je [[Tok podataka|tok podataka]] konkretan prenos podataka između elemenata sistema. Na dijagramu toka protokol može biti upisan uz strelicu.
- [[Aplikacioni protokol|Aplikacioni protokoli]] i [[Transportni protokol|transportni protokoli]] imaju različite uloge. Jedan tok može koristiti protokole sa više slojeva.
- Primeri aplikacionih protokola su [[HTTP]], [[DNS]], [[SSH]], [[MQTT]] i [[FTP]]. [[HTTPS]] označava HTTP komunikaciju zaštićenu [[TLS|TLS-om]]; nije samo drugo ime za HTTP.
- Primeri transportnih protokola su [[TCP]] i [[UDP]]. [[MQTT]] je primer aplikacionog protokola za razmenu poruka.
