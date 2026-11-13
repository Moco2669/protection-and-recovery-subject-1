---
tip: pojam
aliases: [Message Queuing Telemetry Transport, MQTT protocol]
izvor: OASIS, MQTT Version 5.0, odeljci 1.2 i 4 ([standard](https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html))
status: predlog
sloj: jezgro
---
# MQTT (Message Queuing Telemetry Transport)

## Definicija
MQTT je aplikacioni protokol za objavljivanje i pretplatu: klijent objavi poruku na [[MQTT tema|temu]], a [[MQTT broker|broker]] je prosledi klijentima čiji se pretplatnički filter poklapa.

## Primer
U hipotetičkom proširenju Fakturisa, [[Softverski proizvod]] objavi „faktura izdata“ na temu `fakture/izdate`; druga procesna jedinica koja se pretplatila prima poruku preko brokera.

## Napomene
- Klasifikacija u ovoj bazi: aplikacioni protokol jer definiše MQTT pakete, poruke i objava/pretplata operacije. OASIS ga naziva „messaging transport protocol“, ali „transport“ u tom izrazu ne znači transportni sloj TCP/UDP.
- MQTT često koristi [[TCP]]. Obezbeđivanje kriptografske zaštite zavisi od konfiguracije i protokola koji se koriste uz njega.
- QoS 0/1/2 određuje nivoe MQTT isporuke između učesnika u protokolu, ne garantuje da će poslovna radnja biti izvršena tačno jednom.
- Broker i dodatna procesna jedinica su hipotetički elementi, ne osnovna skica Fakturisa.
