---
tip: pojam
aliases: [MQTT Quality of Service, MQTT QoS]
izvor: OASIS, MQTT Version 5.0, odeljak 4.3 ([standard](https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html))
status: predlog
sloj: jezgro
---
# Kvalitet isporuke MQTT (MQTT Quality of Service)

## Definicija
MQTT QoS je nivo protokolskog postupka kojim se uređuje isporuka jedne MQTT poruke između učesnika: 0 najviše jednom, 1 najmanje jednom, 2 tačno jednom.

## Primer
Senzor pošalje poruku sa QoS 1; primalac potvrdi prijem porukom PUBACK. Ako potvrda izostane, pošiljalac može ponoviti objavu, pa aplikacija treba da podnese moguću duplikaciju.

## Napomene
- QoS važi za određenu razmenu između MQTT klijenta i brokera ili brokera i pretplatnika; ne garantuje da je poslovna radnja iza poruke izvršena tačno jednom.
- QoS 0 nema potvrdu, QoS 1 koristi PUBACK, a QoS 2 koristi višekoračnu razmenu (PUBREC/PUBREL/PUBCOMP).
- QoS određuje MQTT, ne [[TCP]]; TCP pouzdanost ne zamenjuje semantiku MQTT QoS-a.

