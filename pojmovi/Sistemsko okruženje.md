---
tip: pojam
aliases: [system environment, execution environment]
izvor: 'Radna sinteza prema NIST SP 800-190, odeljak 2: https://doi.org/10.6028/NIST.SP.800-190'
status: predlog
sloj: temelj
---
# Sistemsko okruženje (system environment)

## Definicija
Sistemsko okruženje je skup [[Sistemski softver|sistemskog softvera]] i podešavanja koji omogućavaju izvršavanje aplikacije i određuju njen pristup resursima uređaja i drugim programima.

## Primer
Ako bi se [[Softverski proizvod|softverski proizvod]] firme [[Fakturis]] izvršavao u Docker kontejneru na Linuxu, Linux, kontejner i njihova podešavanja činili bi njegovo sistemsko okruženje. To je ilustrativna konfiguracija, a ne utvrđena tehnologija firme.

## Napomene
- Odgovara na pitanje: u kakvom okruženju softverska [[Procesna jedinica|procesna jedinica]] radi?
- Sistemski softver uvodi se pre opisa sistemskog okruženja: OS upravlja resursima, a hipervizor omogućava virtuelne mašine.
- Aplikacija može raditi direktno na operativnom sistemu, u [[Kontejner|kontejneru]] ili unutar [[Virtuelna mašina|virtuelne mašine]].
- Ova okruženja mogu se kombinovati: kontejner može raditi unutar virtuelne mašine.
- Za bezbednost su bitni nalog pod kojim aplikacija radi, njegova prava pristupa i ograničenja koja okruženje sprovodi.
- [[Sandbox]] ograničava dozvoljene radnje. To nije četvrta međusobno isključiva opcija pored OS-a, kontejnera i VM-a, već bezbednosno okruženje koje može koristiti ili dopunjavati njihove mehanizme.
- [[Hardverska platforma|Hardverska platforma]] je fizički uređaj. Sistemsko okruženje je softverski sloj koji aplikaciji omogućava i ograničava korišćenje tog uređaja.
