---
tip: pojam
aliases: [Transmission Control Protocol]
izvor: IETF RFC 9293, Transmission Control Protocol ([RFC](https://www.rfc-editor.org/rfc/rfc9293.html))
status: predlog
sloj: jezgro
---
# TCP (Transmission Control Protocol)

## Definicija
TCP je [[Transportni protokol|transportni protokol]] koji krajnjim programima pruža pouzdan, uređen tok bajtova između umreženih računara.

## Primer
Ako pregledač šalje HTTP/1.1 zahtev Fakturisu preko TCP-a, TCP dostavlja bajtove redom i ponavlja prenos kada se deo izgubi, dok HTTP određuje kako se ti bajtovi tumače kao zahtev i odgovor.

Kontraprimer: TCP ne zna da li bajtovi predstavljaju fakturu, HTTP zahtev ili drugi sadržaj. To određuje protokol višeg sloja.

## Napomene
- Pouzdanost TCP prenosa ne znači da je sadržaj bezbedan ili ispravan. Aplikacija i dalje mora da proveri primljene podatke.
- MQTT može koristiti TCP kao protokol prenosa; MQTT uređuje poruke i njihovo prosleđivanje pretplatnicima.
