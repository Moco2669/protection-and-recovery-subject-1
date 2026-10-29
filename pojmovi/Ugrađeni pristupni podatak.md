---
tip: pojam
aliases: [hard-coded credential, hard-coded secret, tajna u izvornom kodu]
izvor: CWE-798 Use of Hard-coded Credentials; CWE-540 Inclusion of Sensitive Information in Source Code
status: predlog
sloj: jezgro
---
# Ugrađeni pristupni podatak (hard-coded credential)

## Definicija
Ugrađeni pristupni podatak je [[Ranjivost|ranjivost]] [[Repozitorijum izvornog koda|repozitorijuma izvornog koda]] i softvera čiji se kod u njemu čuva, u kojoj su lozinka, ključ ili token za pristup nekoj [[Komponenta sistema|komponenti sistema]] ili [[Spoljni servis|spoljnom servisu]] upisani u izvorni kod ili u konfiguracioni fajl koji se čuva zajedno sa kodom.

## Primer
U repozitorijumu aplikacije [[Fakturis]] nalazi se fajl `config/paynet.yml` sa produkcionim API ključem za PayNet, upisanim 2023. godine. Ključ zato znaju svi programeri, svaki bivši programer koji ima kopiju repozitorijuma i svako ko pristupi testnom okruženju. Bezbednosni zahtev kaže da ključ znaju samo aplikacioni server i administrator.

## Napomene
- Brisanje ključa iz poslednje verzije fajla ne otklanja ranjivost, jer ključ ostaje u istoriji izmena. Ključ mora i da se zameni novim.
- Ozbiljnost zavisi od toga šta ključ dozvoljava. Ključ iz primera ima i pravo povraćaja novca, što je posebna ranjivost: [[Prekomerno ovlašćenje]].
