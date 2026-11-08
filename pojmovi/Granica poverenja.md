---
tip: pojam
aliases: [trust boundary, security boundary]
izvor: Microsoft SDL, Secure by Design, "A trust boundary is a logical construct" ([web](https://www.microsoft.com/en-us/securityengineering/sdl/practices/secure-by-design)); Shostack, Experiences Threat Modeling at Microsoft, 2008, odeljak 3.1 ([PDF](https://shostack.org/files/papers/modsec08/Shostack-ModSec08-Experiences-Threat-Modeling-At-Microsoft.pdf))
status: predlog
sloj: jezgro
---
# Granica poverenja (trust boundary)

## Definicija
Granica poverenja je logička linija koja na modelu razdvaja delove sistema sa različitim pretpostavkama o tome ko njima upravlja i koliko su pouzdani.

## Primer
Na [[Dijagram toka podataka|dijagramu toka podataka]] firme [[Fakturis]], isprekidana granica može da obuhvati softverski proizvod, bazu i skladište datoteka kojima upravlja firma. Korisnik i [[Spoljni servis|spoljni servis za naplatu]] ostaju izvan nje. Tok korisnikovih stavki ka proizvodu i poziv proizvoda ka servisu prelaze granicu.

Kontraprimer: svaka linija između dve komponente nije granica poverenja. Ako obe komponente imaju iste pretpostavke poverenja i pod istom kontrolom su, sama njihova povezanost ne stvara takvu granicu.

## Napomene
- Granica poverenja je logička, ne mora da se poklapa sa zidom, ruterom ili fizičkom granicom mreže.
- [[Tok podataka|Tokovi podataka]] koji prelaze granicu zahtevaju posebnu proveru: da li treba autentifikovati učesnika, proveriti pravo pristupa, validirati podatke ili zaštititi komunikaciju.
- Granica sama ne obezbeđuje zaštitu; ona označava mesto na kojem se bezbednosne pretpostavke menjaju.
- Na dijagramu se često prikazuje isprekidanom linijom ili okvirom.
