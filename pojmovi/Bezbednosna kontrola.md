---
tip: pojam
aliases: [security control, kontrola, mera zaštite, safeguard, countermeasure]
izvor: NIST SP 800-53 Rev. 5, Appendix A Glossary, "security control" (OMB A-130); ISO/IEC 27002:2022
status: predavanje
sloj: temelj
---
# Bezbednosna kontrola (security control)

## Definicija
Bezbednosna kontrola je mehanizam ugrađen u [[Komponenta sistema|komponentu sistema]], ili posebna komponenta sistema, kojim organizacija sprečava, otkriva ili ispravlja narušavanje [[Bezbednosno svojstvo|bezbednosnih svojstava]] [[Resurs|resursa]].

## Primer
Kontrole koje firma [[Fakturis]] može da uvede za svoje poznate ranjivosti:

| Kontrola | Komponenta | Dejstvo | Priroda |
|---|---|---|---|
| provera da faktura pripada prijavljenom korisniku pre vraćanja zapisa | web aplikacija | preventivna | tehnička |
| provera potpisa svakog obaveštenja PayNet-a | web aplikacija | preventivna | tehnička |
| pregled svake izmene koda od strane drugog programera pre spajanja | repozitorijum i programeri | preventivna | organizaciona |
| obuka zaposlenih o prepoznavanju lažnih poruka | zaposleni | preventivna | kadrovska |
| zaključan server ormar | server soba | preventivna | fizička |
| upozorenje kada broj odbijenih plaćanja naglo skoči | zapisi o radu | detektivna | tehnička |
| rezervna kopija van mreže firme, uz probu vraćanja jednom mesečno | rezervne kopije | korektivna | tehnička |

## Napomene
- Kontrola se klasifikuje u dve nezavisne dimenzije. Po dejstvu je [[Preventivna kontrola|preventivna]], [[Detektivna kontrola|detektivna]] ili [[Korektivna kontrola|korektivna]]. Po prirodi je [[Tehnička kontrola|tehnička]], [[Organizaciona kontrola|organizaciona]], [[Kadrovska kontrola|kadrovska]] ili [[Fizička kontrola|fizička]].
- Kontrola otklanja [[Ranjivost|ranjivost]] ili prekida i otkriva [[Napad|napad]]. [[Bezbednosni zahtev]] kaže šta mora da važi, a kontrola kako se to postiže.
