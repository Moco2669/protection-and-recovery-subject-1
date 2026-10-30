| **tip** | pojam |
|---|---|
| **aliases** | excessive privileges, unnecessary privileges |
| **izvor** | [MITRE CWE-250 — Execution with Unnecessary Privileges](https://cwe.mitre.org/data/definitions/250.html); [MITRE CWE-269 — Improper Privilege Management](https://cwe.mitre.org/data/definitions/269.html) |

# Prekomerna ovlašćenja (excessive privileges)

## Definicija

Prekomerna ovlašćenja jesu slabost u dodeli prava zbog koje korisnik ili program ima veća prava nego što su potrebna za obavljanje njegovih zadataka.

## Primer

Program za izradu izveštaja o fakturama treba samo da čita podatke iz baze. Ipak, njegov nalog dobije i pravo da briše sve tabele.

Ako napadač preuzme taj nalog, može da obriše fakture, iako brisanje nije potrebno za izradu izveštaja. Nepotrebno pravo brisanja povećava moguću štetu i ugrožava integritet i dostupnost podataka.

## Kontraprimer

Nalog istog programa može samo da čita podatke potrebne za izveštaj. Baza odbija pokušaj brisanja tabela. Za opisani zadatak nalog nema nepotrebna prava brisanja.

## Napomene

Ovlašćenje označava dozvoljenu radnju, poput čitanja dokumenta, menjanja zapisa ili instaliranja programa.

Prekomerna ovlašćenja ne moraju omogućiti početno preuzimanje naloga, ali mogu povećati štetu nakon njegovog preuzimanja.

Administratoru su za neke zadatke potrebna široka prava. Ona nisu prekomerna samo zato što su šira od prava običnog korisnika: procenjuju se prema zadatku i potrebnom trajanju pristupa.
