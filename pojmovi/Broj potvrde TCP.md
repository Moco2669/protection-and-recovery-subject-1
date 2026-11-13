---
tip: pojam
aliases: [TCP acknowledgment number, ACK number]
izvor: IETF RFC 9293, odeljak 3.4 ([RFC](https://www.rfc-editor.org/rfc/rfc9293.html))
status: predlog
sloj: jezgro
---
# Broj potvrde TCP (TCP acknowledgment number)

## Definicija
Broj potvrde TCP (ACK) navodi sledeći broj sekvence koji primalac očekuje od druge strane i kumulativno potvrđuje da su sve prethodne sekvencirane pozicije primljene.

## Primer
Ako server pošalje `ACK=1001`, potvrđuje klijentov SYN sa brojem 1000 i saopštava da je sledeći broj koji očekuje od klijenta 1001.

## Napomene
- ACK broj nije nasumičan: računa se iz sekvence podataka koje je primalac primio i sledeće pozicije koju očekuje. Uslovno se šalje samo kada je ACK zastavica postavljena.
- Svaka strana TCP veze održava svoj redni broj za slanje i ACK broj kojim potvrđuje prijem od druge strane.
- ACK i broj sekvence služe za praćenje prenosa; sami po sebi nisu lozinke niti kriptografski dokaz identiteta.


