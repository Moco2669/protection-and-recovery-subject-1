---
tip: pojam
aliases: [Domain Name System, DNS protocol]
izvor: IETF RFC 1035, Domain Names - Implementation and Specification ([RFC](https://www.rfc-editor.org/rfc/rfc1035.html))
status: predlog
sloj: jezgro
---
# DNS (Domain Name System)

## Definicija
DNS je [[Aplikacioni protokol|aplikacioni protokol]] kojim klijent upitom traži podatke o imenu domena, a DNS server vraća odgovor, na primer mrežnu adresu.

## Primer
Pre nego što se poveže sa `fakturis.example`, pregledač može DNS upitom da zatraži mrežnu adresu tog imena od DNS servera.

Kontraprimer: TCP ili UDP ne prevode ime domena u mrežnu adresu. Oni mogu da prenesu DNS poruke između klijenta i servera.

## Napomene
- DNS može da koristi [[UDP]] ili [[TCP]]. Zato „DNS“ imenuje aplikacioni protokol, a ne transportni protokol.
- DNS primer u ovoj belešci objašnjava opštu upotrebu protokola i ne dodaje DNS server kao utvrđenu komponentu Fakturisa.
