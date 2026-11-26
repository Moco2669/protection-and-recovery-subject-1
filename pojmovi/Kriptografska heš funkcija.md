---
tip: pojam
aliases: [cryptographic hash function, heš funkcija, hash, heš]
izvor: 'NIST FIPS 180-4, Secure Hash Standard; NIST FIPS 202, SHA-3 Standard; NIST CSRC Glossary, hash function'
status: prihvaćeno
sloj: temelj
---
# Kriptografska heš funkcija (cryptographic hash function)

## Definicija
Kriptografska heš funkcija je javna funkcija bez ključa koja podatke proizvoljne dužine preslikava u vrednost fiksne dužine (heš), projektovana tako da bude praktično neizvodljivo naći ulaz za dati heš ili dva različita ulaza sa istim hešom.

## Primer
Postupak objave nove verzije [[Softverski proizvod|softverskog proizvoda]] zapiše SHA-256 heš paketa. Server pre pokretanja ponovo izračuna heš; ako se razlikuje i u jednom bitu, paket je izmenjen posle objave i ne pokreće se.

## Napomene
- Kontrolna suma, na primer u [[UDP zaglavlje|UDP zaglavlju]], nije kriptografski heš: otkriva slučajne greške, ali napadač lako pravi izmenjen sadržaj sa istom sumom.
- Funkcija za koju se nađe praktičan način da se pronađe kolizija ili ulaz za dati heš smatra se razbijenom (MD5, SHA-1).
- Heš nema ključ i ne „dešifruje“ se. Lozinka se iz heša nalazi samo pogađanjem.
- Kolizija heša od n bitova nalazi se posle oko 2^(n/2) pokušaja (rođendanski paradoks); SHA-256 zato daje oko 128 bita otpornosti na kolizije.
- Heš je gradivni blok za [[Kod za autentifikaciju poruke|HMAC]], [[Digitalni potpis|potpis]] i [[Heširanje lozinki|heširanje lozinki]].

## Česti propusti i zaštita
- **MD5 i SHA-1.** Malver Flame (2012) je MD5 kolizijom napravio sertifikat koji je Microsoftova infrastruktura potpisala, pa je mogao da se širi kao lažno Windows ažuriranje. Za SHA-1 su Google i CWI 2017. objavili prvu praktičnu koliziju (SHAttered: dva različita PDF-a, isti heš). *Zaštita:* SHA-256 ili SHA-3 (CWE-328).
- **Heš pored fajla.** Ako napadač provali na sajt za preuzimanje, menja i fajl i objavljeni heš. *Zaštita:* heš sa drugog, nezavisnog mesta ili [[Digitalni potpis|potpis]].
- **`SHA256(tajna || poruka)` kao zaštita poruke.** Kod MD5, SHA-1 i SHA-256, ko zna jedan takav heš, računa ispravan heš za poruku sa dodatkom na kraju, bez tajne ([[Kod za autentifikaciju poruke#Napad produženjem poruke|napad produženjem poruke]]). *Zaštita:* [[Kod za autentifikaciju poruke|HMAC]].
- **Brz heš za lozinke.** MD5 ili SHA-256 lozinke grafička kartica pogađa desetinama milijardi pokušaja u sekundi. *Zaštita:* [[Heširanje lozinki|namenska spora funkcija]].
