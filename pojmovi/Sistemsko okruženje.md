---
tip: pojam
aliases: [system environment, execution environment]
izvor: 'Radna sinteza prema NIST SP 800-190, odeljak 2: https://doi.org/10.6028/NIST.SP.800-190'
status: predlog
sloj: temelj
---
# Sistemsko okruženje (system environment)

## Definicija
Sistemsko okruženje je skup sistemskog softvera i podešavanja koji omogućavaju izvršavanje aplikacije i određuju njen pristup resursima uređaja i drugim programima.

## Primer
Ako bi se [[Softverski proizvod|softverski proizvod]] firme [[Fakturis]] izvršavao u Docker kontejneru na Linuxu, Linux, kontejner i njihova podešavanja činili bi njegovo sistemsko okruženje. To je ilustrativna konfiguracija, a ne utvrđena tehnologija firme.

## Napomene
- Odgovara na pitanje: u kakvom okruženju softverska [[Procesna jedinica|procesna jedinica]] radi?
- Aplikacija može raditi direktno na operativnom sistemu, u kontejneru ili unutar virtuelne mašine.
- Ova okruženja mogu se kombinovati: kontejner može raditi unutar virtuelne mašine.
- Za bezbednost su bitni nalog pod kojim aplikacija radi, njegova prava pristupa i ograničenja koja okruženje sprovodi.
- [[Hardverska platforma|Hardverska platforma]] je fizički uređaj. Sistemsko okruženje je softverski sloj koji aplikaciji omogućava i ograničava korišćenje tog uređaja.
