---
tip: pojam
aliases: [security misconfiguration, default credentials, fabrička lozinka]
izvor: OWASP Top 10:2025, A02:2025 Security Misconfiguration (https://owasp.org/Top10/2025/); CWE-1392 Use of Default Credentials
status: predlog
sloj: jezgro
---
# Pogrešna bezbednosna konfiguracija (security misconfiguration)

## Definicija
Pogrešna bezbednosna konfiguracija je [[Ranjivost|ranjivost]] [[Komponenta sistema|komponente sistema]] u kojoj su njena podešavanja, za razliku od dizajna ili koda, postavljena tako da dozvoljavaju radnje koje [[Bezbednosni zahtev|bezbednosni zahtevi]] ne dozvoljavaju.

## Primer
Pogrešne konfiguracije u firmi [[Fakturis]]:
- administratorski panel [[Mrežni prolaz|mrežnog prolaza]] dostupan je sa interneta na portu 8080, a lozinka je ostala fabrička (`admin`). Svako ko pronađe panel može da promeni pravila zaštitnog zida;
- Office na [[Poslovni računar|poslovnim računarima]] pokreće makroe iz dokumenata preuzetih sa interneta;
- nginx na aplikacionom [[Server|serveru]] u porukama o greškama prikazuje svoju verziju i putanje fajlova.

U sva tri slučaja softver radi ispravno. Problem je u tome kako je podešen.

## Napomene
- Najčešći uzrok je zadržavanje podrazumevanih podešavanja proizvođača, koja su izabrana da bi uređaj ili program odmah radio, a ne da bi bio bezbedan.
- Skup kontrola kojima se podešavanja sužavaju na ono što je potrebno naziva se hardening sistema.
