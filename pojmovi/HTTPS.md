---
tip: pojam
aliases: [HTTP Secure, Hypertext Transfer Protocol Secure]
izvor: IETF RFC 9110, HTTP Semantics, odeljak 4.2.2 ([RFC](https://www.rfc-editor.org/rfc/rfc9110.html))
status: predlog
sloj: jezgro
---
# HTTPS (HTTP over TLS)

## Definicija
HTTPS označava [[HTTP|HTTP komunikaciju]] preko veze zaštićene protokolom [[TLS|TLS]], tako da se proverava identitet servera, a podaci se štite od čitanja i izmene tokom prenosa.

## Primer
Ako pregledač korisnika otvori stranicu Fakturisa sa adresom koja počinje sa `https://`, zahtev za izdavanje fakture i odgovor proizvoda razmenjuju se kroz TLS-om zaštićenu komunikaciju.

Kontraprimer: HTTP bez TLS-a ne pruža HTTPS zaštitu, čak i kada se koristi isti format zahteva i odgovora.

## Napomene
- RFC 9110 precizno opisuje `https` kao URI šemu koja označava HTTP komunikaciju zaštićenu TLS-om. U svakodnevnom govoru se HTTPS često naziva protokolom, ali ne uvodi drugačiju semantiku zahteva od HTTP-a.
- HTTPS štiti kanal prenosa; sam po sebi ne određuje da li korisnik sme da izda fakturu niti da li je sadržaj zahteva bezbedan za obradu.
- U uobičajenim kombinacijama HTTP/1.1 ili HTTP/2 koristi TLS preko [[TCP|TCP-a]]. Konkretna verzija HTTP-a i prenosni protokol Fakturisa nisu utvrđeni u studiji slučaja.
