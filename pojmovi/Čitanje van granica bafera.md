---
tip: pojam
aliases: [out-of-bounds read, buffer over-read, buffer under-read]
izvor: 'MITRE CWE-125, Out-of-bounds Read: https://cwe.mitre.org/data/definitions/125.html; RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajd 127'
status: prihvaćeno
sloj: jezgro
---
# Čitanje van granica bafera (out-of-bounds read)

## Definicija
Čitanje van granica bafera je [[Prostorna memorijska ranjivost|prostorna memorijska ranjivost]] zbog koje program može da pročita podatke iza kraja ili ispred početka [[Bafer|bafera]].

## Primer
Zahtev navodi da je naziv kupca dugačak 500 bajtova, a šalje samo 10. Modul za generisanje PDF faktura u [[Fakturis]] uzima dužinu iz zahteva, pročita 490 bajtova susedne memorije i upiše ih u PDF koji korisnik dobija, zajedno sa podacima drugih kupaca.

## Napomene
- Čitanje ne menja podatke. Ishod je [[Narušavanje poverljivosti podataka]].
- Heartbleed je primer sa predavanja RBS 07 (slajdovi 61 i 127).
- Upis van granica bafera je [[Prekoračenje bafera|prekoračenje]] ili [[Potkoračenje bafera|potkoračenje]].
