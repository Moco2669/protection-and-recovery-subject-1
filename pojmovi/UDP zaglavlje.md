---
tip: pojam
aliases: [UDP header, UDP datagram header]
izvor: IETF RFC 768 ([RFC](https://www.rfc-editor.org/rfc/rfc768.html))
status: predlog
sloj: jezgro
---
# UDP zaglavlje (UDP header)

## Definicija
UDP zaglavlje je osmobajtni početak [[UDP datagram|UDP datagrama]] sa izvornim portom, odredišnim portom, dužinom i kontrolnom sumom.

## Primer
DNS upit ima UDP zaglavlje sa izvornim privremenim portom klijenta i odredišnim portom DNS usluge 53; posle osam bajtova zaglavlja slede podaci DNS poruke.

## Napomene
- Polje dužine računa celo UDP datagramsko područje: zaglavlje plus podaci; minimalna vrednost je 8 bajtova.
- Kontrolna suma pomaže da se otkriju greške u prenosu; sama nije kriptografski dokaz identiteta ni zaštita od namerne izmene.
- UDP ne sadrži ACK polje niti sam ponavlja izgubljeni datagram.

