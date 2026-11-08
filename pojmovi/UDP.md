---
tip: pojam
aliases: [User Datagram Protocol]
izvor: IETF RFC 768, User Datagram Protocol ([RFC](https://www.rfc-editor.org/rfc/rfc768.html))
status: predlog
sloj: jezgro
---
# UDP (User Datagram Protocol)

## Definicija
UDP je [[Transportni protokol|transportni protokol]] koji omogućava programima da šalju datagrame uz mali broj pravila za isporuku; sam UDP ne garantuje da će datagram stići niti da će stići redosledom kojim je poslat.

## Primer
DNS klijent može da pošalje upit DNS serveru preko UDP-a. Ako odgovor ne stigne, DNS klijent ili druga komponenta protokola može da pokuša ponovo.

Kontraprimer: TCP pruža pouzdan i uređen tok bajtova. UDP ne pruža te garancije, iako aplikacija koja ga koristi može zasebno da doda ponovno slanje ili proveru redosleda.

## Napomene
- UDP čuva granice datagrama, dok TCP krajnjem programu pruža tok bajtova.
- DNS može koristiti i TCP; UDP nije jedini prenosni protokol za DNS.
