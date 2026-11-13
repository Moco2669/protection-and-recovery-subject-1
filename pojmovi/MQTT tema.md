---
tip: pojam
aliases: [MQTT topic, topic, tema u MQTT-u]
izvor: OASIS, MQTT Version 5.0, odeljci 1.3 i 4 ([standard](https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html))
status: predlog
sloj: jezgro
---
# MQTT tema (MQTT topic)

## Definicija
MQTT tema je UTF-8 niz koji označava kategoriju ili putanju objavljenih poruka, a pretplatnički filter teme određuje koje poruke [[MQTT broker|broker]] prosleđuje pretplatniku.

## Primer
Hipotetički senzor objavi temperaturu na `fakturis/servis/temperatura`; kontrolna tabla pretplaćena na isti filter dobija poruku od brokera.

## Napomene
- Tema je oznaka za rutiranje poruke, ne nužno fizički uređaj ili objekat.
- Pretplatnički filter može koristiti `+` i `#`; objavljena tema nije filter.
- Broker i senzor u primeru nisu deo osnovne skice Fakturisa.

