---
tip: pojam
aliases: [TCP three-way handshake, TCP handshake, TCP connection handshake]
izvor: IETF RFC 9293, odeljak 3.5 ([RFC](https://www.rfc-editor.org/rfc/rfc9293.html))
status: predlog
sloj: jezgro
---
# TCP uspostavljanje veze (TCP three-way handshake)

## Definicija
TCP uspostavljanje veze je trokorakna razmena SYN, SYN-ACK i ACK kojom strane sinhronizuju svoje početne brojeve sekvence i potvrđuju da su obe strane dostupne za vezu.

## Primer
Klijent šalje `SYN seq=1000`; server odgovara `SYN,ACK seq=7000 ack=1001`; klijent šalje `ACK seq=1001 ack=7001`. Brojevi 1000 i 7000 su ilustrativni [[TCP početni redni broj|početni brojevi]].

## Napomene
- Svaka strana bira svoj početni redni broj. ACK određuje se iz primljene sekvence druge strane; nije nasumičan.
- SYN zauzima jednu poziciju sekvence, zato je ACK za SYN sa 1000 jednak 1001. Prazan ACK sam ne zauzima sekvencu.
- TCP handshake uspostavlja transportnu vezu; zaštita podataka zahteva poseban mehanizam/protokol.
