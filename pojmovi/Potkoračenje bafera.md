---
tip: pojam
aliases: [buffer underflow, buffer underwrite, buffer underrun, upis ispred početka bafera]
izvor: 'MITRE CWE-124, Buffer Underwrite (Buffer Underflow): https://cwe.mitre.org/data/definitions/124.html'
status: prihvaćeno
sloj: jezgro
---
# Potkoračenje bafera (buffer underflow)

## Definicija
Potkoračenje bafera je [[Prostorna memorijska ranjivost|prostorna memorijska ranjivost]] zbog koje program može da upiše podatke ispred početka [[Bafer|bafera]].

## Primer
Modul za generisanje PDF faktura u [[Fakturis]] skida razmake sa kraja naziva kupca idući unazad. Ako je naziv sastavljen samo od razmaka, indeks prođe početak bafera i završni znak se upiše ispred njega.

## Napomene
- CWE beleži da se „underflow“ ponekad koristi i za čitanje ispred početka bafera (CWE-127). Ovde je to [[Čitanje van granica bafera|čitanje van granica]].
- U sistemima i mrežama buffer underflow obično znači da se bafer prazni brže nego što se puni, na primer pri snimanju CD-a. To nije ranjivost.
- Celobrojno potkoračenje je treći pojam, koji se jednako zove.
- Upis iza kraja bafera je [[Prekoračenje bafera|prekoračenje]].
