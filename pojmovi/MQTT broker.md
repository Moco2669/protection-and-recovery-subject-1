---
tip: pojam
aliases: [MQTT broker, MQTT server, broker]
izvor: OASIS, MQTT Version 5.0, odeljci 1.2 i 4 ([standard](https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html))
status: predlog
sloj: jezgro
---
# MQTT broker (MQTT broker)

## Definicija
MQTT broker je [[Serverski program|serverski program]] koji prima objave i pretplate klijenata i prosleđuje objave pretplatnicima čiji se filter [[MQTT tema|teme]] poklapa.

## Primer
U hipotetičkom sistemu senzor objavi `22.4 °C` na temu `fakturis/servis/temperatura`; broker prosledi poruku dashboard-u koji se pretplatio.

## Napomene
- Broker je programska uloga, ne računar. OASIS specifikacija koristi naziv MQTT server.
- MQTT klijenti razmenjuju poruke preko brokera.

