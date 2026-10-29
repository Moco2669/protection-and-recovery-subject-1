---
tip: pojam
aliases: [preventive control]
izvor: ISO/IEC 27002:2022, 4.2, atribut "control type": preventive
status: predlog
sloj: temelj
---
# Preventivna kontrola (preventive control)

## Definicija
Preventivna kontrola je [[Bezbednosna kontrola|bezbednosna kontrola]] koja deluje pre narušavanja [[Bezbednosno svojstvo|bezbednosnog svojstva]], tako što otklanja [[Ranjivost|ranjivost]] ili onemogućava da neki korak [[Napad|napada]] uspe.

## Primer
Preventivne kontrole koje firma [[Fakturis]] može da uvede za svoje poznate ranjivosti:
- aplikacija pre vraćanja fakture proverava da li ona pripada prijavljenom korisniku;
- pretraga kupaca koristi parametrizovane upite;
- aplikacija odbacuje svako obaveštenje o uplati bez ispravnog potpisa PayNet-a;
- stranica za plaćanje dozvoljava najviše pet pokušaja po fakturi na sat;
- server ormar je zaključan, a ključ je kod Stefana.

Kontraprimer: upozorenje Stefanu kada broj odbijenih plaćanja u minuti pređe dvadeset ne sprečava ni jedan pokušaj, nego ga otkriva. To je [[Detektivna kontrola|detektivna kontrola]].
