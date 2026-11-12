---
tip: pojam
aliases: [data at rest, information at rest, podatak u mirovanju]
izvor: NIST SP 800-53 Rev. 5, kontrola SC-28 Protection of Information at Rest
status: predlog
sloj: temelj
---
# Podaci u mirovanju (data at rest)

## Definicija
Podaci u mirovanju su podaci sačuvani na nekoj komponenti sistema dok ih nijedna [[Procesna jedinica|procesna jedinica]] ne obrađuje i nijedan [[Tok podataka|tok podataka]] ne prenosi.

## Primer
Zapis fakture koji je [[Softverski proizvod|softverski proizvod]] firme [[Fakturis]] upisao u [[Baza podataka|bazu podataka]] i PDF datoteka iste fakture u [[Skladište datoteka|skladištu datoteka]] su podaci u mirovanju. Kada korisnik sutradan otvori fakturu, proizvod je čita i šalje mu je. Ista faktura je tada u obradi, a zatim u prenosu.

Kontraprimer: stavke fakture dok putuju od korisnika do proizvoda nisu podaci u mirovanju. Njih štiti zaštita prenosa, a ne zaštita skladišta.

## Napomene
- Isti podatak prolazi kroz mirovanje, obradu i prenos. Zaštita jednog stanja ne štiti ostala.
- U mirovanju nisu samo podaci u [[Skladište podataka|skladištima podataka]]. Kopije u [[Sistem za rezervne kopije|sistemu za rezervne kopije]] i dokumenti na disku [[Poslovni računar|poslovnog računara]] takođe su podaci u mirovanju.
- Kako konkretna skladišta drže podatke u mirovanju opisuje odeljak **Čuvanje na disku** u beleškama vrsta skladišta, na primer [[Relaciona baza podataka]] i [[Deljeni mrežni folder]].
- Pretnje nad podacima u mirovanju opisane su u odeljcima o skladištu podataka u beleškama [[Narušavanje poverljivosti podataka]], [[Narušavanje integriteta podataka]] i [[Narušavanje dostupnosti resursa]].
