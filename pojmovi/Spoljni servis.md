---
tip: pojam
aliases: [external service, external system service]
izvor: NIST SP 800-53 Rev. 5, "external system service" (https://csrc.nist.gov/glossary/term/external_information_system_service)
status: prihvaćeno
sloj: temelj
---
# Spoljni servis (external service)

## Definicija
Spoljni servis je servis kojim upravlja druga organizacija, van sistema organizacije, a koji [[Softverski proizvod|softverski proizvod]] poziva da bi obavio deo svog posla.

## Primer
[[Fakturis]] za naplatu faktura koristi dva spoljna servisa, oba tuđe firme. [[Softverski proizvod|Softverski proizvod]] poziva jedan od njih. Nijedan nije komponenta Fakturisa, i podaci o kartici kupca u sistem ne ulaze.

Kontraprimer: internet provajder je tuđa firma, ali proizvod ga ne poziva da obavi deo posla. On nije spoljni servis u ovom smislu.

## Napomene
- Spoljni servis stoji van granice sistema. Deo proizvoda koji ga poziva je [[Interfejs ka spoljnom servisu|interfejs ka spoljnom servisu]].
