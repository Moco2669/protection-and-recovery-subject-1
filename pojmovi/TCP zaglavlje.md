---
tip: pojam
aliases: [TCP header, TCP segment header]
izvor: IETF RFC 9293, odeljak 3.1 ([RFC](https://www.rfc-editor.org/rfc/rfc9293.html))
status: predlog
sloj: jezgro
---
# TCP zaglavlje (TCP header)

## Definicija
TCP zaglavlje su kontrolna polja na početku [[TCP segment|TCP segmenta]] koja opisuju portove, pozicije bajtova, potvrde, prijemni prozor i druge kontrole prenosa.

## Primer
Za HTTP vezu TCP zaglavlje sadrži izvorni privremeni port klijenta, odredišni port servera 80, sekvencu/ACK, zastavice i prozor; posle zaglavlja sledi deo HTTP poruke.

## Napomene
- Obavezna polja su: izvorni i odredišni port, broj sekvence, broj potvrde, data offset, rezervisani bitovi, zastavice, prozor, kontrolna suma i hitni pokazivač. Minimum je 20 bajtova; opcije mogu zaglavlje produžiti.
- Data offset izražava veličinu zaglavlja u 32-bitnim rečima; vrednost 5 znači 20 bajtova, a 10 znači 40 bajtova.
- Prozor oglašava prostor za prijem, ne veličinu segmenta niti broj bajtova do sledeće ACK poruke.
- SYN otvara vezu, ACK označava validno ACK polje, a FIN učestvuje u zatvaranju.
- Podaci aplikacije nisu polje TCP zaglavlja; dolaze posle zaglavlja kao payload segmenta.
