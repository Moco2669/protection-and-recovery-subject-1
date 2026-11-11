---
tip: pojam
aliases: [container, application container]
izvor: 'Docker Docs, What is a container?: https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/'
status: predlog
sloj: temelj
---
# Kontejner (container)

## Definicija
Kontejner je okruženje u kojem se aplikacija izvršava odvojeno od drugih aplikacija, koristeći isti operativni sistem.

## Primer
Ako bi se serverski deo [[Softverski proizvod|softverskog proizvoda]] firme [[Fakturis]] pokretao u Docker kontejneru, njegov kod i potrebne biblioteke bili bi smešteni u okruženje izdvojeno od drugih aplikacija. Kontejner bi koristio jezgro Linuxa na kojem radi. Ovo je ilustrativna konfiguracija.

## Napomene
- Kontejner je jedan od načina organizovanja [[Sistemsko okruženje|sistemskog okruženja]] aplikacije.
- Docker je primer tehnologije za rad sa kontejnerima.
- Jezgro je osnovni deo operativnog sistema koji upravlja resursima uređaja. Kontejneri dele jezgro operativnog sistema na kojem rade.
- Za razliku od virtuelne mašine, kontejner nema sopstveno jezgro operativnog sistema.
- Kontejner može raditi unutar virtuelne mašine.
- Odvojeno izvršavanje znači ograničen pristup drugim aplikacijama i njihovim podacima, a ne potpunu nezavisnost. Pristup datotekama, mreži i uređajima zavisi od podešavanja i prava procesa.
