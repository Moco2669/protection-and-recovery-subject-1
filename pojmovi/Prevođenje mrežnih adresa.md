---
tip: pojam
aliases: [NAT, Network Address Translation]
izvor: IETF RFC 2663, IP Network Address Translator (NAT) Terminology and Considerations ([RFC](https://www.rfc-editor.org/rfc/rfc2663.html)); RFC 3022, Traditional NAT ([RFC](https://www.rfc-editor.org/rfc/rfc3022.html))
status: predlog
sloj: jezgro
---
# Prevođenje mrežnih adresa (Network Address Translation, NAT)

## Definicija
Prevođenje mrežnih adresa (NAT) je funkcija mrežnog uređaja koja menja IP adresu, a ponekad i TCP/UDP port u paketima koji prelaze između mreža, uz čuvanje preslikavanja kako bi odgovori mogli biti vraćeni odgovarajućem uređaju.

## Primer
Ilustrativno, kada bi [[Mrežni prolaz|mrežni prolaz]] Fakturisa koristio NAPT, izlazna veza `10.0.0.20:49152` mogla bi spolja izgledati kao `203.0.113.5:53001`. Mrežni prolaz pamti preslikavanje i koristi ga da odgovor vrati na `10.0.0.20:49152`. Ove adrese su primeri; takva konfiguracija nije utvrđena za Fakturis.

## Napomene
- Osnovni NAT menja IP adresu. NAPT (Network Address Port Translation), često nazvan PAT, uz adresu menja i transportni port kako bi više uređaja moglo deliti jednu javnu adresu.
- NAT nije isto što i [[Mrežni prolaz|mrežni prolaz]]: prolaz povezuje mreže i može prosleđivati ili filtrirati saobraćaj; NAT menja adrese/portove u saobraćaju.
- NAT sam po sebi nije šifrovanje, autentifikacija ni zamena za zaštitni zid. To što uređaj koristi privatnu adresu ne znači da su podaci zaštićeni.
- NAT može otežati neke dolazne veze i aplikacije koje prenose adrese u sadržaju, zato FTP aktivni režim može imati problem iza NAT-a; vidi [[FTP aktivni režim]] i [[FTP pasivni režim]].
