---
tip: pojam
aliases: [security misconfiguration, default credentials, fabrička lozinka]
izvor: OWASP Top 10:2025, A02:2025 Security Misconfiguration (https://owasp.org/Top10/2025/); CWE-1392 Use of Default Credentials
status: predlog
sloj: jezgro
---
# Pogrešna bezbednosna konfiguracija (security misconfiguration)

## Definicija
Pogrešna bezbednosna konfiguracija je [[Slabost|slabost]] u kojoj su podešavanja [[Komponenta sistema|komponente sistema]], za razliku od njenog dizajna ili koda, postavljena tako da dozvoljavaju više nego što [[Bezbednosni zahtev|bezbednosni zahtevi]] traže.

## Primer
Pogrešne konfiguracije u firmi [[Fakturis]]:
- administratorski panel rutera dostupan je sa interneta, a lozinka je ostala fabrička;
- Office na poslovnim računarima pokreće makroe iz dokumenata preuzetih sa interneta;
- nginx u porukama o greškama prikazuje svoju verziju i putanje fajlova na serveru.

U sva tri slučaja softver radi ispravno. Problem je u tome kako je podešen.

## Napomene
- Najčešći uzrok je zadržavanje podrazumevanih podešavanja proizvođača, koja su izabrana da bi uređaj ili program odmah radio, a ne da bi bio bezbedan.
- Skup kontrola kojima se podešavanja sužavaju na ono što je potrebno naziva se hardening sistema.
