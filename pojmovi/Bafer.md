---
tip: pojam
aliases: [buffer]
izvor: 'RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajd 62'
status: prihvaćeno
sloj: temelj
---
# Bafer (buffer)

## Definicija
Bafer je neprekidan deo memorije određene veličine, namenjen za smeštanje niza podataka.

## Primer
Modul za generisanje PDF faktura u [[Softverski proizvod|softverskom proizvodu]] firme [[Fakturis]] zauzima 64 bajta memorije za naziv kupca. Tih 64 bajta su bafer: u njega staje najviše 64 bajta.

## Napomene
- U sistemima i mrežama „bafer“ često znači privremeno skladište podataka između dva procesa. Ovde je bitan samo memorijski region sa početkom i krajem.
