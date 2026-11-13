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

## Gde postaviti granicu
1. Odredi opseg sistema i na dijagramu prikaži glavne elemente i tokove.
2. Za svaki element utvrdi ko njime upravlja, ko mu pristupa i koja pravila/kontrole važe.
3. Grupši elemente sa sličnim pretpostavkama. Postavi granicu između grupa ako se menja ko može da pristupi ili menja podatke, ko odobrava pristup, ili koje zaštitne kontrole proveravaju tok. Primer razlike: aplikacija koristi ograničen nalog prema bazi, dok DBA nalozi imaju zasebna, šira prava.
4. Označi tokove koji prelaze liniju i proceni njihove bezbednosne zahteve.

**Kada je crtati:** pri izradi početnog modela, nakon što su opseg, elementi i tokovi poznati, a pre analize pretnji. Ponovo je razmotri ako se promene upravljanje, prava ili kontrole. „Gde“ označava mesto na modelu; „kada“ označava fazu rada.

## Primeri
- **Korisnik → Fakturis:** korisnikom i uređajem ne upravlja firma, pa tok stavki fakture prelazi granicu sistema firme.
- **Proizvod ↔ PostgreSQL, ista zona:** u osnovnoj skici baza je na aplikacionom serveru; ako nad obe komponente važe slična pravila i kontrole, mogu biti u istoj zoni. Sama podela na komponente ne zahteva granicu.
- **Proizvod ↔ PostgreSQL, odvojene zone:** hipotetički, bazom upravlja poseban DBA tim, pristup bazi je ograničen na aplikacioni server, a aplikacija koristi nalog sa manjim pravima. Različita administracija/privilegije opravdavaju unutrašnju granicu. Ova konfiguracija nije utvrđena za Fakturis.
- Broj uređaja ne određuje broj zona: dve mašine mogu imati iste kontrole, a jedna mašina može sadržati procese sa različitim privilegijama.


