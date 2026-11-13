---
tip: pojam
aliases: [communication security protocol, security protocol]
izvor: IETF RFC 4251, The Secure Shell Protocol Architecture ([RFC](https://www.rfc-editor.org/rfc/rfc4251.html))
status: predlog
sloj: jezgro
---
# Protokol za zaštitu komunikacije (communication security protocol)

## Definicija
Protokol za zaštitu komunikacije utvrđuje kako učesnici autentifikuju drugu stranu i štite poruke od prisluškivanja ili izmene, dok značenje zaštićenih poruka određuje protokol koji koristi tu zaštitu.

## Primer
SSH uspostavlja zaštićen kanal između klijenta i serverskog programa, a zatim autentifikuje korisnika i prenosi komande. SSH protokolna porodica obavlja i zaštitu i aplikacijske funkcije udaljenog pristupa.

## Napomene
- Ova je funkcionalna kategorija, ne jedan od sedam OSI slojeva.
- [[QUIC]] je transportni protokol koji istovremeno pruža kriptografsku zaštitu veze.
- [[SSH]] sadrži transportni podprotokol za zaštitu kanala, kao i podprotokole za prijavu i kanale.
- Uloge protokola mogu se preklapati.
