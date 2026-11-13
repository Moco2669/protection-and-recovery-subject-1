---
tip: pojam
aliases: [TCP sequence number, sequence number]
izvor: IETF RFC 9293, odeljak 3.4 ([RFC](https://www.rfc-editor.org/rfc/rfc9293.html))
status: predlog
sloj: jezgro
---
# Broj sekvence TCP (TCP sequence number)

## Definicija
Broj sekvence TCP segmenta označava poziciju prvog bajta podataka u prostoru rednih brojeva; SYN i FIN takođe zauzimaju po jednu poziciju.

## Primer
Klijent šalje SYN sa početnim brojem 1000. SYN zauzima jednu poziciju, pa server šalje `ACK=1001`, što znači da očekuje sledeću poziciju klijenta od 1001.

## Napomene
- Broj sekvence broji bajtove, ne segmente; primalac ne mora unapred znati koliko će segmenata stići.
- ACK broj je sledeći broj sekvence koji primalac očekuje.
- Početna vrednost bira se zasebno po vezi; vidi [[TCP početni redni broj]].

