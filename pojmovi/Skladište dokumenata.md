---
tip: pojam
aliases: [file storage, file share, NAS, deljeni folder]
izvor: CIS Critical Security Controls v8, Glossary, "servers" (file servers); nema posebne standardne definicije
status: predlog
sloj: temelj
---
# Skladište dokumenata (file storage)

## Definicija
Skladište dokumenata je [[Komponenta sistema|komponenta sistema]] u kojoj se čuvaju datoteke, kao što su ugovori, izveštaji i generisane fakture, i koja ih preko mreže stavlja na raspolaganje [[Zaposleni|zaposlenima]] i drugim komponentama.

## Primer
Skladište dokumenata firme [[Fakturis]] je mrežni uređaj za skladištenje (NAS) u server sobi. U njemu su PDF fakture koje generiše [[Web aplikacija|web aplikacija]], kao i poslovni dokumenti firme: ugovori sa korisnicima i partnerima, finansijski izveštaji i ponude. Zaposleni mu pristupaju kao deljenom folderu `\\nas\dokumenti` sa svojih [[Poslovni računar|poslovnih računara]].

Kontraprimer: dokument koji Jelena drži samo na svom laptopu nije u skladištu dokumenata, iako je poslovni dokument. Zato se ne kopira ni u rezervne kopije.

## Napomene
- Za razliku od [[Baza podataka|baze podataka]], skladište ne zna šta je unutar datoteke. Prava pristupa se zato zadaju po folderima, a ne po pojedinačnim podacima.
- Karakteristična ranjivost: svi zaposleni imaju pravo čitanja i pisanja nad celim deljenim folderom ([[Prekomerno ovlašćenje]]).
