---
tip: pojam
aliases: [insufficient logging and monitoring, security logging and alerting failures]
izvor: OWASP Top 10:2025, A09:2025 Security Logging and Alerting Failures (https://owasp.org/Top10/2025/); CWE-778 Insufficient Logging
status: predlog
sloj: jezgro
---
# Nedovoljno beleženje i praćenje (insufficient logging and monitoring)

## Definicija
Nedovoljno beleženje i praćenje je [[Slabost|slabost]] u kojoj [[Komponenta sistema|komponenta sistema]] ne beleži radnje potrebne da se [[Napad|napad]] otkrije ili da se radnja pripiše onome ko ju je izvršio, ili u kojoj se zabeleženo ne pregleda i ne izaziva upozorenje.

## Primer
Aplikacija [[Fakturis]] beleži samo greške. Prijave, neuspele prijave, storniranja i promene statusa faktura ne beleže se. Zapisi se čuvaju sedam dana na aplikacionom serveru i niko ih ne pregleda. Posledice:
- kada korisnik porekne storno fakture, firma ne može da dokaže ko ga je izvršio, pa je narušena [[Neporecivost|neporecivost]];
- korisnik koji je tri nedelje redom čitao tuđe fakture preko `/api/fakture/{id}` nije primećen;
- napadač koji preuzme aplikacioni server može da obriše i zapise koji postoje.

## Napomene
- Ova slabost retko omogućava napad, ali sprečava da se napad otkrije i da se posle njega utvrdi šta se dogodilo. Detektivne kontrole zavise od zapisa koje ona uskraćuje.
