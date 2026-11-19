---
tip: pojam
aliases: [container, application container]
izvor: 'Docker Docs, What is a container?: https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/'
status: predlog
sloj: temelj
---
# Kontejner (container)

## Definicija
Kontejner je izdvojeno okruženje za izvršavanje jednog ili više procesa aplikacije sa njenim zavisnostima, koje deli jezgro operativnog sistema domaćina.

## Primer
Ako bi se serverski deo [[Softverski proizvod|softverskog proizvoda]] firme [[Fakturis]] pokretao u Docker kontejneru, njegov kod i potrebne biblioteke bili bi smešteni u okruženje izdvojeno od drugih aplikacija. Kontejner bi koristio jezgro Linuxa na kojem radi. Ovo je ilustrativna konfiguracija.

## Napomene
- Kontejner je jedan od načina organizovanja [[Sistemsko okruženje|sistemskog okruženja]] aplikacije.
- Docker je primer tehnologije za rad sa kontejnerima.
- Jezgro je osnovni deo operativnog sistema koji upravlja resursima uređaja. Kontejneri dele jezgro operativnog sistema na kojem rade.
- Za razliku od [[Virtuelna mašina|virtuelne mašine]], kontejner nema sopstveno jezgro operativnog sistema. Može sadržati biblioteke i druge korisničke delove OS-a.
- Kontejner može raditi unutar virtuelne mašine.
- [[Sandbox]] opisuje bezbednosnu namenu: ograničiti šta program sme da uradi. Kontejner označava način izdvajanja izvršnog okruženja uz deljeno jezgro. Kontejner se može koristiti u realizaciji sandboxa, ali njegova ograničenja zavise od podešavanja.
- Docker kontejner pokrenut sa širokim pravima i pristupom osetljivim datotekama domaćina nije automatski bezbedno okruženje za nepouzdan kod.
- Odvojeno izvršavanje znači ograničen pristup drugim aplikacijama i njihovim podacima, a ne potpunu nezavisnost. Pristup datotekama, mreži i uređajima zavisi od podešavanja i prava procesa.
