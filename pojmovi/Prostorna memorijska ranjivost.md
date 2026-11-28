---
tip: pojam
aliases: [spatial memory safety vulnerability]
izvor: 'RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajdovi 154 i 157; Szekeres, Payer, Wei, Song, SoK: Eternal War in Memory, IEEE S&P 2013: https://www.ieee-security.org/TC/SP2013/papers/4977a048.pdf'
status: prihvaćeno
sloj: jezgro
---
# Prostorna memorijska ranjivost (spatial memory safety vulnerability)

## Definicija
Prostorna memorijska ranjivost je [[Memorijska ranjivost|memorijska ranjivost]] zbog koje program može da pristupi memoriji van granica [[Memorijski objekat|memorijskog objekta]] preko pokazivača izvedenog iz tog objekta.

## Primer
Modul za generisanje PDF faktura u [[Softverski proizvod|softverskom proizvodu]] firme [[Fakturis]] kopira naziv kupca u [[Bafer|bafer]] od 64 bajta. Naziv od 200 bajtova navodi modul da upiše 136 bajtova van granica bafera.

## Napomene
- Predavanje RBS 07 ovu klasu naziva „buffer overflow“. Obuhvata upis i čitanje, iza kraja i ispred početka.
- Vrste: [[Prekoračenje bafera]], [[Potkoračenje bafera]] i [[Čitanje van granica bafera]].
