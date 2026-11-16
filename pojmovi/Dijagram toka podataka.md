---
tip: pojam
aliases: [data flow diagram, DFD]
izvor: Shostack, Experiences Threat Modeling at Microsoft, 2008, odeljak 3.1 i tabela 1 ([PDF](https://shostack.org/files/papers/modsec08/Shostack-ModSec08-Experiences-Threat-Modeling-At-Microsoft.pdf))
status: predlog
sloj: jezgro
---
# Dijagram toka podataka (data flow diagram)

## Definicija
Dijagram toka podataka je grafički model sistema koji prikazuje procesne jedinice koje obrađuju podatke, skladišta u kojima se podaci čuvaju, spoljne entitete sa kojima sistem razmenjuje podatke i usmerene tokove između njih.

## Primer
Dijagram izdavanja fakture u Fakturisu prikazuje korisnika kao spoljni entitet, softverski proizvod kao procesnu jedinicu, bazu i skladište datoteka kao skladišta. Strelice označavaju stavke fakture, zapis i datoteku fakture.

## Napomene
- Osnovni simboli predstavljaju [[Procesna jedinica|procesne jedinice]], [[Skladište podataka|skladišta podataka]], [[Spoljni entitet|spoljne entitete]] i [[Tok podataka|tokove podataka]].
- U konvenciji ove baze svaki tok ima procesnu jedinicu na jednom kraju; skladište ili spoljni entitet ne povezuju se direktno bez procesa koji obrađuje ili prenosi podatke.
- Strelica prikazuje smer toka; opis može navesti vrstu podataka i protokol.
- U bezbednosnom modelovanju na dijagram se dodaju [[Granica poverenja|granice poverenja]]. Dijagram opisuje logičke uloge: proces i baza mogu biti na istoj mašini i ipak odvojeni elementi.
- Grafički model je model kretanja i obrade podataka u sistemu, ne samo mapa mrežnih veza.

