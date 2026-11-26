---
tip: pojam
aliases: [digital certificate, public key certificate, X.509, sertifikat javnog ključa, infrastruktura javnih ključeva, public key infrastructure, PKI, sertifikaciono telo, certificate authority, CA, lanac sertifikata, korenski sertifikat]
izvor: 'IETF RFC 5280, Internet X.509 Public Key Infrastructure Certificate and CRL Profile; NIST CSRC Glossary, public key infrastructure'
status: prihvaćeno
sloj: jezgro
---
# Digitalni sertifikat (digital certificate)

## Definicija
Digitalni sertifikat je podatak koji vezuje [[Asimetrična kriptografija|javni ključ]] za identitet vlasnika, npr. ime domena, tokom perioda važenja, a koji je [[Digitalni potpis|potpisao]] izdavalac čijem javnom ključu proveravač veruje.

## Primer
[[Softverski proizvod]] poziva API [[Spoljni servis|spoljnog servisa]] za plaćanje. Programer je pri testiranju isključio proveru sertifikata (`requests.post(url, verify=False)`) i tako je ostalo u produkciji. Veza je šifrovana, ali se ne proverava sa kim: napadač na mreži predstavi se kao servis za plaćanje svojim sertifikatom, prima pozive sa API ključem i vraća „plaćanje uspešno“ ([[Napad posrednikom]]). Sa uključenom proverom, lažni sertifikat ne prolazi.

## Napomene
- Glavna polja: subjekt i alternativna imena (SAN), javni ključ, izdavalac, period važenja, namena ključa, potpis izdavaoca.
- Sertifikat je javan; vrednost mu je u potpisu, a server dokazuje da poseduje privatni ključ.
- Provera obuhvata potpis i ceo lanac do korena, rok važenja i ime.
- Rokovi važenja se skraćuju (CA/Browser Forum, 2025: postepeno do 47 dana 2029), pa se sertifikati obnavljaju automatski (ACME, RFC 8555).

## Infrastruktura javnih ključeva
Infrastruktura javnih ključeva (PKI) je skup sertifikacionih tela, odnosno izdavalaca sertifikata kojima učesnici veruju, i pravila i postupaka kojima se sertifikati izdaju, proveravaju i opozivaju, tako da učesnik koji veruje malom broju korenskih ključeva može da proveri čiji je bilo koji drugi javni ključ.

Pregledač ne zna unapred ključ servera `example.com`, ali ima ugrađenu listu korenskih sertifikata kojima veruje. Server šalje svoj sertifikat i sertifikat posredničkog tela; pregledač proverava lanac: koren potpisuje posrednika, posrednik potpisuje sertifikat za `example.com`.

- Sertifikaciono telo (CA) proverava da podnosilac kontroliše domen i potpisuje sertifikat. Korenski ključevi su van mreže.
- Opoziv ukradenog sertifikata (CRL, OCSP) u praksi slabo radi, pa se sve više oslanja na kratke rokove važenja.
- Certificate Transparency: svaki javno poverljiv sertifikat upisuje se u javne dnevnike, pa vlasnik domena otkriva sertifikat koji nije tražio.
- Bezbednost zavisi od najslabijeg tela kojem pregledač veruje, jer svako od njih može da izda sertifikat za bilo koji domen.

## Česti propusti i zaštita
- **Isključena provera** (`verify=False`, `curl -k`, Java `TrustManager` koji prihvata sve) (CWE-295). *Zaštita:* provera nikad isključena u kodu; za testove se koristi testno sertifikaciono telo.
- **Provera bez imena**: potpis je ispravan, ali sertifikat glasi na drugi domen. *Zaštita:* standardna provera biblioteke, ne ručna.
- **Istekao sertifikat** obara uslugu i navikava korisnike da klikću kroz upozorenja. *Zaštita:* automatska obnova i nadzor roka.
- **Kompromitovano sertifikaciono telo.** Provaljen DigiNotar (2011) izdao je lažne sertifikate za Google domene, korišćene za prisluškivanje korisnika u Iranu. *Zaštita:* uklanjanje tela iz pregledača (DigiNotar je zatim bankrotirao) i Certificate Transparency, uvedena delom zbog ovog slučaja.
- **Nepoznat korenski sertifikat na računaru.** Lenovo je 2015. na laptopove preinstalirao Superfish, koji je dodavao sopstveni koren, sa istim privatnim ključem na svim uređajima; ključ je brzo izvučen, pa je svako mogao da presreće HTTPS tih korisnika. *Zaštita:* dodavanje korena na [[Poslovni računar|poslovne računare]] je organizaciona odluka, uz popis dozvoljenih korena.
- **Interno sertifikaciono telo bez zaštite**: ključ na deljenom disku omogućava izdavanje sertifikata za bilo koji interni servis. *Zaštita:* ključ internog sertifikacionog tela van mreže ili u HSM-u.
