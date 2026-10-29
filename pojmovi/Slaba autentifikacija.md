---
tip: pojam
aliases: [weak authentication, authentication failures, single-factor authentication]
izvor: OWASP Top 10:2025, A07:2025 Authentication Failures (https://owasp.org/Top10/2025/); CWE-308 Use of Single-factor Authentication; CWE-521 Weak Password Requirements
status: predlog
sloj: jezgro
---
# Slaba autentifikacija (weak authentication)

## Definicija
Slaba autentifikacija je [[Ranjivost|ranjivost]] [[Sistem za upravljanje nalozima|sistema za upravljanje nalozima]] u kojoj prijava ne pruža dovoljno pouzdan dokaz da je osoba ona za koju se izdaje, pa napadač koji sazna ili pogodi lozinku može da se prijavi kao ona.

## Primer
U firmi [[Fakturis]] na GitLab i na administratorski deo aplikacije prijavljuje se samo lozinkom. Direktorijum zaposlenih prihvata lozinke od osam znakova bez ikakvih drugih uslova, a Stefan za GitLab koristi istu lozinku kao na jednom forumu sa koga su lozinke procurele prošle godine. Napadač koji isproba procurele lozinke može da uđe u GitLab kao administrator.

## Napomene
- Prijava samo lozinkom (jednofaktorska) je ranjivost upravo za naloge sa velikim ovlašćenjima. Kontrola je prijava sa dodatnim faktorom, na primer kodom sa telefona.
- Razgraničenje: slaba autentifikacija znači da sistem ne zna pouzdano ko se prijavio. [[Neispravna kontrola pristupa]] znači da sistem zna ko je, ali mu dozvoljava više nego što sme.
