---
tip: pojam
aliases: [Secure Shell, SSH protocol]
izvor: IETF RFC 4251, The Secure Shell (SSH) Protocol Architecture ([RFC](https://www.rfc-editor.org/rfc/rfc4251.html))
status: predlog
sloj: jezgro
---
# SSH (Secure Shell)

## Definicija
SSH je skup komunikacionih protokola za bezbednu udaljenu prijavu i druge mrežne usluge preko mreže kojoj se ne može unapred verovati.

## Primer
Ako administrator Stefan pristupa serveru Fakturisa preko SSH-a, SSH protokoli mogu da obezbede šifrovanu vezu, provere identitet servera i omoguće autentifikaciju administratora.

Kontraprimer: udaljena prijava na server preko nezaštićenog protokola nije SSH, čak i kada administrator koristi istu komandnu liniju.

## Napomene
- SSH nije samo jedan jednostavan protokol. Arhitektura obuhvata protokol za zaštićeni transport, autentifikaciju korisnika i povezivanje kanala.
- „Transportni“ deo SSH-a nije isto što i [[Transportni protokol|transportni protokol]] poput [[TCP]]. SSH se uobičajeno prenosi preko TCP veze.
- Primer je ilustrativan. Udaljeni pristup Fakturisu u studiji slučaja nije vezan za SSH.
