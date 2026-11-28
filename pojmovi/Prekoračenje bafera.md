---
tip: pojam
aliases: [buffer overflow, buffer overrun, prelivanje bafera, prepunjavanje bafera]
izvor: 'NIST CSRC Glossary, buffer overflow (NIST SP 800-28 Version 2, CNSSI 4009-2022): https://csrc.nist.gov/glossary/term/buffer_overflow; MITRE CWE-120, Buffer Copy without Checking Size of Input (Classic Buffer Overflow): https://cwe.mitre.org/data/definitions/120.html; RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajdovi 62 i 64'
status: prihvaćeno
sloj: jezgro
---
# Prekoračenje bafera (buffer overflow)

## Definicija
Prekoračenje bafera je [[Prostorna memorijska ranjivost|prostorna memorijska ranjivost]] zbog koje program može da upiše podatke iza kraja [[Bafer|bafera]] u koji upisuje.

## Primer
Korisnik u polje za naziv kupca unese 200 bajtova. Modul za generisanje PDF faktura u [[Fakturis]] ih kopira u bafer od 64 bajta, pa 136 bajtova prepiše susedne podatke u memoriji.

Kontraprimer: ako bi modul samo pročitao 136 bajtova iza kraja bafera, to je [[Čitanje van granica bafera|čitanje van granica]], a ne prekoračenje.

## Napomene
- Bafer može biti na [[Stek|steku]] ili na [[Heap|heap-u]], a CWE ih vodi kao zasebne slučajeve (CWE-121, CWE-122).
- Predavanje RBS 07 koristi „buffer overflow“ za sve prostorne greške. Ovde označava samo upis iza kraja bafera.
- Upis ispred početka bafera je [[Potkoračenje bafera|potkoračenje]].
- [[Zaštita steka kanarincem]] može da otkrije prekoračenje bafera na steku ako ono promeni zaštitnu vrednost; ne sprečava sam upis van granica.
