---
tip: pojam
aliases: [corrective control]
izvor: ISO/IEC 27002:2022, 4.2, atribut "control type": corrective
status: predlog
sloj: temelj
---
# Korektivna kontrola (corrective control)

## Definicija
Korektivna kontrola je [[Bezbednosna kontrola|bezbednosna kontrola]] koja posle narušavanja [[Bezbednosno svojstvo|bezbednosnog svojstva]] vraća [[Resurs|resurs]] u stanje u kom to svojstvo ponovo važi, ili ograničava štetu koja je nastala.

## Primer
Korektivne kontrole koje firma [[Fakturis]] može da uvede:
- svake noći pravi se kopija baze i skladišta dokumenata na disk koji nije dostupan iz mreže firme, a Stefan jednom mesečno proba da iz nje vrati podatke. Posle ransomware napada podaci se vraćaju za četiri sata;
- kada se otkrije da je API ključ za PayNet bio u repozitorijumu, Stefan ga poništava kod PayNet-a i postavlja novi;
- fakture koje su označene kao plaćene bez potvrde PayNet-a vraćaju se u status „neplaćeno“.

Kontraprimer: rezervne kopije na serveru za kopije, koji je u istoj mreži kao i poslovni računari, ransomware je šifrovao zajedno sa originalima. Kopije postoje, ali ne mogu da vrate podatke, pa u tom napadu ne deluju kao korektivna kontrola.

## Napomene
- Kontrola se svrstava po trenutku kada deluje, a ne kada se priprema. Rezervna kopija se pravi unapred, ali deluje tek posle narušavanja, pa je korektivna.
