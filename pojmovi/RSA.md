---
tip: pojam
aliases: [Rivest–Shamir–Adleman, RSA]
izvor: IETF RFC 8017, PKCS #1: RSA Cryptography Specifications ([RFC](https://www.rfc-editor.org/rfc/rfc8017.html))
status: predlog
sloj: jezgro
---
# RSA (RSA public-key cryptography)

## Definicija
RSA je algoritamska porodica asimetrične kriptografije koja koristi matematički povezan javni i privatni ključ za operacije kao što su digitalno potpisivanje i, u odgovarajućim protokolima, šifrovanje ključeva ili podataka.

## Primer
U sistemu koji koristi sertifikate, server može imati RSA javni ključ u sertifikatu, a privatnim ključem potpisati dokaz identiteta. Klijent proverava potpis javnim ključem iz validiranog sertifikata.

## Napomene

- RSA se može koristiti za potpise; konkretna upotreba i dogovor ključeva zavise od protokola.

