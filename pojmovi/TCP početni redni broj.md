---
tip: pojam
aliases: [TCP initial sequence number, ISN]
izvor: IETF RFC 6528, Defending against Sequence Number Attacks ([RFC](https://www.rfc-editor.org/rfc/rfc6528.html))
status: predlog
sloj: jezgro
---
# TCP početni redni broj (TCP initial sequence number)

## Definicija
TCP početni redni broj je početna vrednost koju strana izabere za brojeve sekvence nove veze; druga strana je saznaje kroz SYN i potvrđuje kroz ACK.

## Primer
Klijent bira 1000, server 7000. Server šalje `SYN,ACK` sa `SEQ=7000, ACK=1001`; klijent potvrđuje serverov SYN sa `ACK=7001`.

## Napomene
- Brojevi su ilustrativni. Svaka strana bira početnu vrednost nezavisno, a stvarne vrednosti nisu fiksne niti se unapred dogovaraju ručno.
- Početne vrednosti se biraju tako da različite veze ne koriste stalno iste početne brojeve.


