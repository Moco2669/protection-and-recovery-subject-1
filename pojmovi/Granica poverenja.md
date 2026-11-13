---
tip: pojam
aliases: [trust boundary, security boundary]
izvor: Microsoft SDL, Secure by Design ([web](https://www.microsoft.com/en-us/securityengineering/sdl/practices/secure-by-design)); Shostack, 2008, odeljak 3.1 ([PDF](https://shostack.org/files/papers/modsec08/Shostack-ModSec08-Experiences-Threat-Modeling-At-Microsoft.pdf))
status: predlog
sloj: jezgro
---
# Granica poverenja (trust boundary)

## Definicija
Granica poverenja je logička linija na modelu koja razdvaja zone sistema sa različitim pretpostavkama o tome ko upravlja elementima, ko im pristupa i koje kontrole važe.

## Primer
Na [[Dijagram toka podataka|dijagramu]] Fakturisa, okvir obuhvata softverski proizvod i bazu pod kontrolom firme. Korisnik i spoljni servis za naplatu su izvan okvira; tokovi između njih i proizvoda prelaze granicu.

## Napomene
- Granica nije automatski zid, ruter, granica računara niti svaka veza. Sama po sebi ne pruža zaštitu.
- Tok koji prelazi granicu je mesto za procenu potrebe da se proveri identitet, pravo pristupa, ulazni podaci i zaštita prenosa.



