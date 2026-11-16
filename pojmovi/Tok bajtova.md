---
tip: pojam
aliases: [byte stream, stream of bytes]
izvor: IETF RFC 9293, Transmission Control Protocol ([RFC](https://www.rfc-editor.org/rfc/rfc9293.html))
status: predlog
sloj: jezgro
---
# Tok bajtova (byte stream)

## Definicija
Tok bajtova je niz bajtova u kojem se čuva njihov redosled, ali se ne čuvaju granice pojedinačnih poruka koje je pošiljalac predao transportnom sloju.

## Primer
[[TCP]] prenosi bajtove HTTP zahteva redom; prijemni program dobija niz bajtova i HTTP parsira granice zahteva iz svog formata.

## Napomene
- TCP segmenti su transportne jedinice, ali primalac aplikaciji vidi uređen tok bajtova, ne obavezno isti raspored poruka ili segmenata koji je pošiljalac koristio.
- [[UDP]] prenosi datagrame i čuva granice datagrama.

