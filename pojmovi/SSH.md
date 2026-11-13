---
tip: pojam
aliases: [Secure Shell, SSH protocol]
izvor: IETF RFC 4251, The Secure Shell (SSH) Protocol Architecture ([RFC](https://www.rfc-editor.org/rfc/rfc4251.html))
status: predlog
sloj: jezgro
---
# SSH (Secure Shell)

## Definicija
SSH je protokolarna porodica za bezbednu udaljenu prijavu i druge mrežne usluge preko nepouzdane mreže; obuhvata zaštićeni transportni podprotokol, autentifikaciju korisnika i protokol za multipleksiranje kanala.

## Primer
Administrator Stefan pokreće SSH klijent na poslovnom računaru da bi se prijavio na aplikacioni [[Server|server]] Fakturisa. Klijent proverava host ključ, zatim se korisnik autentifikuje, pa otvara shell kanal.

## Napomene
- SSH se uobičajeno prenosi preko [[TCP|TCP-a]]. „SSH transportni sloj“ je komponenta SSH arhitekture, ne transportni protokol internet steka.
- SSH serverska uloga je program na server računaru. Razlikovati [[Serverski program]] od [[Server|računara-servera]].
- Neproveren host ključ omogućava lažnom serveru da se predstavi kao pravi; krađa korisničkog ključa ili kompromitovanje endpointa takođe ugrožava sesiju.
- SSH kanali mogu nositi terminal, komande i prosleđivanje portova.



