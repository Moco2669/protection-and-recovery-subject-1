---
tip: pojam
aliases: [data flow, tok podataka]
izvor: Shostack, Experiences Threat Modeling at Microsoft, 2008, tabela 1 ([PDF](https://shostack.org/files/papers/modsec08/Shostack-ModSec08-Experiences-Threat-Modeling-At-Microsoft.pdf))
status: predlog
sloj: temelj
---
# Tok podataka (data flow)

## Definicija
Tok podataka je usmeren prenos podataka između elemenata [[Dijagram toka podataka|dijagrama toka podataka]]; u konvenciji ove baze jedan kraj toka je uvek [[Procesna jedinica|procesna jedinica]], a drugi može biti druga procesna jedinica, [[Skladište podataka|skladište podataka]] ili [[Spoljni entitet]].

## Primer
Pri izdavanju fakture, korisnik šalje stavke [[Softverski proizvod|softverskom proizvodu]], a proizvod prenosi zapis do baze i datoteku do skladišta datoteka. Svaka strelica prikazuje poseban tok i smer prenosa.

## Napomene
- Strelica prikazuje smer. Oznaka može navesti prenete podatke i [[Protokol|protokol]].
- Tok nije mrežna veza: veza je put/mehanizam, tok je prenos podataka između modelovanih elemenata.
- Tok može ulaziti u sistem, izlaziti iz njega ili povezivati njegove elemente.
- Tokovi koji prelaze [[Granica poverenja|granicu poverenja]] izdvajaju se za bezbednosnu analizu.

