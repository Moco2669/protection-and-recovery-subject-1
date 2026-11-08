---
tip: pojam
aliases: [data flow diagram, DFD]
izvor: Shostack, Experiences Threat Modeling at Microsoft, 2008, odeljak 3.1 i tabela 1 ([PDF](https://shostack.org/files/papers/modsec08/Shostack-ModSec08-Experiences-Threat-Modeling-At-Microsoft.pdf); Microsoft SDL, Secure by Design ([web](https://www.microsoft.com/en-us/securityengineering/sdl/practices/secure-by-design)))
status: predlog
sloj: jezgro
---
# Dijagram toka podataka (data flow diagram)

## Definicija
Dijagram toka podataka je grafički model koji prikazuje gde se podaci obrađuju, gde se čuvaju i kako se prenose između [[Procesna jedinica|procesnih jedinica]], [[Skladište podataka|skladišta podataka]] i [[Spoljni entitet|spoljnih entiteta]].

## Primer
Dijagram izdavanja fakture u firmi [[Fakturis]] prikazuje korisnika kao spoljni entitet, softverski proizvod kao procesnu jedinicu, a bazu i skladište datoteka kao skladišta podataka. Strelice pokazuju da stavke stižu do proizvoda, a zapis i datoteka fakture odlaze u odgovarajuća skladišta.

Kontraprimer: dijagram koji prikazuje samo da su server i baza podataka mrežno povezani nije dijagram toka podataka, jer ne pokazuje koji se podaci prenose niti gde se obrađuju ili čuvaju.

## Napomene
- Osnovni elementi su [[Procesna jedinica|procesne jedinice]], [[Skladište podataka|skladišta podataka]], [[Tok podataka|tokovi podataka]] i [[Spoljni entitet|spoljni entiteti]].
- Strelica predstavlja tok i pokazuje smer prenosa. Uz nju se mogu navesti vrsta podataka i [[Protokol|protokol]].
- U bezbednosnom modelovanju, na dijagram se mogu dodati [[Granica poverenja|granice poverenja]].
- Dijagram prikazuje logičke uloge; dve komponente mogu raditi na istom računaru, a ipak biti odvojeni elementi modela.
