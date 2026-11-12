---
tip: pojam
aliases: [source code repository, repozitorijum, Git, GitLab]
izvor: nema standardne bezbednosne definicije; srodno: NIST SP 800-218 (SSDF), praksa PS.1 Protect All Forms of Code
status: predlog
sloj: temelj
---
# Repozitorijum izvornog koda (source code repository)

## Definicija
Repozitorijum izvornog koda je [[Skladište podataka|skladište podataka]] koje čuva izvorni kod sa celom istorijom izmena i iz kojeg se nove verzije softvera proveravaju i objavljuju.

## Primer
Programeri firme [[Fakturis]] čuvaju kod [[Softverski proizvod|softverskog proizvoda]] na internom GitLab [[Server|serveru]]. Svaka izmena ostaje u istoriji, sa imenom autora. Posle provere, nova verzija se objavljuje na aplikacioni server.

Kontraprimer: lokalna kopija koda na Milanovom laptopu sadrži isti kod, ali iz nje se ništa ne objavljuje i ona nije izvor istine. Ona je deo njegovog [[Poslovni računar|poslovnog računara]].

## Napomene
- Repozitorijum sadrži više od koda: konfiguracione fajlove, skripte za objavljivanje, ponekad i pristupne podatke. Ko može da menja repozitorijum, može da promeni i ono što se izvršava na serveru.
- Provera i objava nove verzije, kad se crta na dijagramu toka podataka, jeste [[Procesna jedinica|procesna jedinica]] koja čita ovo skladište. Sam repozitorijum je mesto gde kod stoji.

**Čuvanje na disku.** Svaka kopija repozitorijuma sadrži celu istoriju izmena. Ono što je obrisano iz poslednje verzije ostaje u istoriji.

**Pristup.** Programeri pristupaju preko SSH ključa ili pristupnog tokena, sa pravom čitanja ili i upisa.

**Komande.** Preuzimanje kopije (clone), upis izmena (commit, push) i spajanje grana. Objava nove verzije čita repozitorijum.

Razlika od [[Skladište zapisa|skladišta zapisa]]: oba čuvaju istoriju, ali repozitorijum čuva ono što će se izvršavati i menjaju ga ljudi namerno, dok skladište zapisa čuva trag o onome što se već desilo.
