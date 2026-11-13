---
tip: pojam
aliases: [external entity, external actor]
izvor: Shostack, Experiences Threat Modeling at Microsoft, 2008, tabela 1, "external entity" ([PDF](https://shostack.org/files/papers/modsec08/Shostack-ModSec08-Experiences-Threat-Modeling-At-Microsoft.pdf))
status: predlog
sloj: temelj
---
# Spoljni entitet (external entity)

## Definicija
Spoljni entitet je osoba ili sistem izvan opsega modelovanog sistema koji sa njegovim komponentama razmenjuje podatke.

## Primer
Pri izdavanju fakture u firmi [[Fakturis]], korisnik je spoljni entitet jer šalje stavke fakture [[Softverski proizvod|softverskom proizvodu]]. Spoljni servis za naplatu je takođe spoljni entitet: proizvod mu šalje poziv, a servis vraća odgovor.

Kontraprimer: [[Baza podataka|baza podataka]] u kojoj Fakturis čuva zapis fakture nije spoljni entitet. Ona je komponenta sistema firme.

## Napomene
- Spoljni entitet može biti osoba ili sistem; ne mora biti servis koji poziva softverski proizvod.
- [[Spoljni servis|Spoljni servis]] je uži pojam: njime upravlja druga organizacija, a proizvod ga poziva da obavi deo posla.
- Spoljni entitet se prikazuje kao element [[Dijagram toka podataka|dijagrama toka podataka]]. U ovoj notaciji prikazuje se pravougaonikom.

