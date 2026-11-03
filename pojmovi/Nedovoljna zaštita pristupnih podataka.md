---
tip: pojam
aliases: ["insufficiently protected credentials"]
izvor: "MITRE CWE-522: Insufficiently Protected Credentials, https://cwe.mitre.org/data/definitions/522.html"
---

# Nedovoljna zaštita pristupnih podataka (insufficiently protected credentials)

## Definicija

Nedovoljna zaštita pristupnih podataka je [[Slabost|slabost]] pri kojoj komponenta čuva ili razmenjuje tajne za prijavu ili pristup drugoj komponenti na način koji omogućava njihovo pribavljanje učesniku koji nema pravo da ih sazna.

## Primer

Program koristi tajni pristupni podatak za pozivanje druge komponente. U posmatranom scenariju programer sme da čita razvojna podešavanja, ali ne i produkcionu tajnu. Ako se ta tajna sačuva u njemu dostupnoj kopiji podešavanja, konkretna ranjivost omogućava neovlašćeno čitanje pristupnog podatka u komponenti koja čuva tu kopiju. Kasnije korišćenje pribavljene tajne jeste druga radnja u mogućem nizu napada, a ne isto što i njeno otkrivanje.

## Napomene

Tajna može biti dostupna kroz različita mesta čuvanja ili tokove: podešavanja, izvorni kod, rezervnu kopiju ili zapis o radu. Način otkrivanja zavisi od mesta čuvanja i pravila pristupa.

Prenos tajne može pripadati i pojmu [[Izostanak zaštite poverljivosti prenosa]]; dve klasifikacije se preklapaju jer jedna prati vrstu resursa, a druga njegovo kretanje.

Mesto čuvanja tajne i prava koja tajna omogućava različita su pitanja. Nepotrebno široka prava mogu povećati posledice, ali nisu uslov da otkrivanje tajne bude problem.
