---
tip: pojam
aliases: [TCP window, receive window, TCP receive window]
izvor: IETF RFC 9293, odeljak 3.8.6 ([RFC](https://www.rfc-editor.org/rfc/rfc9293.html))
status: predlog
sloj: jezgro
---
# TCP prozor (TCP receive window)

## Definicija
TCP prozor je opseg brojeva sekvence koje je primalac trenutno spreman da prihvati; polje prozora oglašava raspoloživi opseg u bajtovima, uz moguće skaliranje dogovoreno opcijom Window Scale.

## Primer
Server šalje `ACK=1001` i prozor od 4000 bajtova, oglašavajući naredni opseg koji je spreman da primi. Pošiljalac može poslati te bajtove pre potvrde njihovog prijema.

## Napomene
- Prozor ne znači „broj bajtova nakon kojih se šalje potvrda“ i ne određuje veličinu segmenta.
- To je kontrola toka: primalac objavljuje prijemni kapacitet. ACK potvrđuje primljeni niz; učestalost ACK-ova nije veličina prozora.
- Jedan prozor može obuhvatiti više TCP segmenata.

