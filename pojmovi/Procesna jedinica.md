---
tip: pojam
aliases: [process, DFD process]
izvor: Shostack, Experiences Threat Modeling at Microsoft, 2008, tabela 1, "process" (kod)
status: predlog
sloj: temelj
---
# Procesna jedinica (process)

## Definicija
Procesna jedinica je komponenta sistema koja od podataka koje prima podatke, transformiše ih i šalje ih dalje.

## Primer
Pri izdavanju fakture u firmi [[Fakturis]] [[Softverski proizvod|softverski proizvod]] je procesna jedinica: od stavki koje korisnik unese pravi zapis fakture i datoteku.

Kontraprimer: [[Baza podataka|baza podataka]] u koju taj zapis stiže nije procesna jedinica. Ona ga čuva, a ne pravi drugi podatak od njega.

## Napomene
- Ovo nije centralna procesna jedinica računara. U dijagramima toka podataka engleski termin je process.
- Nije poslovni proces. Poslovni proces je sled rada. Procesna jedinica je jedno mesto koje od ulaza pravi izlaz.
- [[Skladište podataka|Skladište podataka]] čuva podatke. Procesna jedinica ih obrađuje.
- Na dubljem dijagramu procesna jedinica može biti deo proizvoda, ne samo proizvod kao celina. Klasa koja poziva [[Spoljni servis|spoljni servis]] crta se tako, a nije poseban pojam.
- [[Zaposleni sa pristupom|Zaposleni sa pristupom]] koji od ulaznih podataka pravi druge, na dijagramu takođe može biti procesna jedinica. Lice ili servis van sistema nisu.
