---
tip: pojam
aliases: [TCP segment, TCP packet]
izvor: IETF RFC 9293, Transmission Control Protocol ([RFC](https://www.rfc-editor.org/rfc/rfc9293.html))
status: predlog
sloj: jezgro
---
# TCP segment (TCP segment)

## Definicija
TCP segment je jedinica koju TCP šalje kroz IP: sadrži TCP zaglavlje i deo toka bajtova koji se prenosi, a može nositi i samo kontrolne informacije bez podataka.

## Primer
HTTP zahtev se može podeliti na više TCP segmenata. Svaki segment nosi broj sekvence za svoj deo bajtova; TCP na prijemu sastavlja uređeni tok za aplikaciju.

## Napomene
- U govoru se ponekad kaže „TCP paket“, ali „segment“ je precizniji naziv TCP jedinice; IP prenosi te segmente u IP paketima.
- TCP segment nije isto što i HTTP zahtev niti jedna cela korisnička poruka.

