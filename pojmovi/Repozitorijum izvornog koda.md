---
tip: pojam
aliases: [source code repository, repozitorijum, Git, GitLab]
izvor: nema standardne bezbednosne definicije; srodno: NIST SP 800-218 (SSDF), praksa PS.1 Protect All Forms of Code
status: predlog
sloj: temelj
---
# Repozitorijum izvornog koda (source code repository)

## Definicija
Repozitorijum izvornog koda je softverska [[Komponenta sistema|komponenta sistema]] koja čuva izvorni kod sa celom istorijom izmena i iz koje se nove verzije softvera proveravaju i objavljuju.

## Primer
Programeri firme [[Fakturis]] čuvaju kod aplikacije na internom GitLab [[Server|serveru]]. Svaka izmena ostaje u istoriji, sa imenom autora. Posle svake izmene GitLab CI pokreće testove u testnom okruženju, virtuelnoj mašini sa kopijom produkcione baze, i ako testovi prođu, postavlja novu verziju na aplikacioni server.

Kontraprimer: lokalna kopija koda na Milanovom laptopu sadrži isti kod, ali iz nje se ništa ne objavljuje i ona nije izvor istine. Ona je deo njegovog [[Poslovni računar|poslovnog računara]].

## Napomene
- Repozitorijum sadrži više od koda: konfiguracione fajlove, skripte za objavljivanje, ponekad i pristupne podatke. Ko može da menja repozitorijum, može da promeni i ono što se izvršava na produkcionom serveru.
- U [[Fakturis]] je produkcioni API ključ za PayNet upisan u `config/paynet.yml`. Ključ je [[Resurs|resurs]] firme, a repozitorijum je komponenta u kojoj se taj resurs nalazi.
