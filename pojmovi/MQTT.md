---
tip: pojam
aliases: [Message Queuing Telemetry Transport, MQTT protocol]
izvor: OASIS, MQTT Version 5.0, odeljci 1.2 i 4 ([standard](https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html))
status: predlog
sloj: jezgro
---
# MQTT (Message Queuing Telemetry Transport)

## Definicija
MQTT je protokol za razmenu poruka po obrascu objavljivanja i pretplate: klijent objavi poruku na temu, a server je prosledi klijentima koji su se pretplatili na tu temu.

## Primer
U hipotetičkom proširenju firme [[Fakturis]], [[Softverski proizvod|softverski proizvod]] objavi poruku „faktura izdata“ na temu `fakture/izdate`. Druga procesna jedinica koja se pretplatila na tu temu prima poruku od MQTT servera, koji se naziva posrednik (broker).

Kontraprimer: pri uobičajenoj HTTP razmeni klijent šalje zahtev serveru i dobija odgovor na taj zahtev. MQTT klijenti objavljuju poruke na teme, a posrednik ih prosleđuje pretplaćenim klijentima.

## Napomene
- MQTT je [[Aplikacioni protokol|aplikacioni protokol]] u slojevitoj podeli ove baze: uređuje poruke i objavljivanje/pretplatu, dok se za prenos može koristiti [[TCP]]. OASIS specifikacija ga naziva „messaging transport protocol“, pa „transport“ u tom nazivu ne treba mešati sa transportnim slojem TCP-a i UDP-a.
- MQTT definiše tri nivoa kvaliteta isporuke (QoS): najviše jednom, najmanje jednom i tačno jednom između MQTT učesnika u toj razmeni. To samo po sebi ne garantuje da će poslovna radnja koju poruka pokrene biti izvršena tačno jednom.
- OASIS specifikacija ne zahteva jedan protokol prenosa, ali navodi TCP/IP kao mogući prenos; TLS može da zaštiti vezu. Tačna konfiguracija nije utvrđena za Fakturis.
- Posrednik i druga procesna jedinica u primeru su hipotetički elementi i nisu deo osnovne skice Fakturisa.
