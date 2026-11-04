---
tip: pojam
aliases: [data flow]
izvor: Shostack, Experiences Threat Modeling at Microsoft, 2008, tabela 1, "data flow" (kako informacija teče između elemenata)
status: predlog
sloj: temelj
---
# Tok podataka (data flow)

## Definicija
Tok podataka je prenosni kanal čiji je jedan kraj [[Procesna jedinica|procesna jedinica]], a drugi kraj procesna jedinica, [[Skladište podataka|skladište podataka]], lice van sistema ili [[Spoljni servis|spoljni servis]].

## Primer
Pri izdavanju fakture u firmi [[Fakturis]] jedan tok podataka nosi stavke od korisnika do [[Softverski proizvod|proizvoda]], drugi nosi zapis od proizvoda do [[Baza podataka|baze podataka]], a treći nosi poziv naplate od proizvoda do [[Spoljni servis|spoljnog servisa]].

Kontraprimer: to što su mrežni prolaz i server povezani nije tok podataka. Tok nastaje kad se tim putem podaci zaista prenesu.

## Napomene
- Dijagram toka podataka slaže se od procesnih jedinica, skladišta podataka, tokova i lica ili servisa van sistema. Služi kasnijem opisu slabosti, napada i bezbednosnih kontrola.
- Strelica može ići i od skladišta ka procesnoj jedinici, kad procesna jedinica čita sačuvano. I tada je jedan kraj procesna jedinica.
