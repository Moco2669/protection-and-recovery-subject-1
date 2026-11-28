---
tip: pojam
aliases: [crypto agility, cryptographic agility, kripto agilnost]
izvor: 'NIST CSWP 39, Considerations for Achieving Crypto Agility: Strategies and Practices (decembar 2025, ažurirano 2026): https://doi.org/10.6028/NIST.CSWP.39; IETF RFC 7696 (BCP 201)'
status: prihvaćeno
sloj: front
---
# Kriptografska agilnost (crypto agility)

## Definicija
Kriptografska agilnost je sposobnost sistema i organizacije da zamene oslabljen ili zastareo kriptografski algoritam, parametre ili implementaciju bez prekida rada i bez ponovnog projektovanja sistema.

## Primer
Dve aplikacije treba da pređu sa bcrypt-a na Argon2id:

- **Agilna:** zapis lozinke nosi algoritam i parametre (`$2b$12$...`, `$argon2id$v=19$...`). Pri sledećoj uspešnoj prijavi aplikacija proveri stari zapis i upiše novi. Bez migracije baze i bez promene lozinki.
- **Neagilna:** kolona `lozinka_hash` ne kaže kojim je algoritmom napravljena, a poziv `bcrypt` je na petnaest mesta u kodu. Prelaz traži izmenu svih mesta i nagađanje koji red je kojim algoritmom.

Isto važi za šifrovane podatke: oznaka verzije ključa i algoritma (`v2:`) ispred svake šifrovane vrednosti omogućava postepen prelaz.

## Napomene
- **Kriptografski inventar** (gde se koji algoritam, ključ, sertifikat i biblioteka koriste; za softver CBOM) je prvi korak: ne može se zameniti ono za šta se ne zna gde je.
- **Apstrakcija:** kod poziva „šifruj zapis“ ili „potpiši“ iz jednog mesta, a algoritam se bira konfiguracijom.
- **Organizacija:** ko prati preporuke, ko odlučuje o zameni i koliko dugo stari algoritam ostaje dozvoljen. NIST CSWP 39 agilnost opisuje i kao zrelost organizacije.
- Neposredan povod je prelaz na [[Postkvantna kriptografija|postkvantnu kriptografiju]], koji zahvata svaku razmenu ključeva i svaki potpis u sistemu.

## Česti propusti i zaštita
- **Agilnost bez zaštite izbora.** Više podržanih algoritama znači više prilika za [[Napad degradiranjem verzije]]. *Zaštita:* autentifikovan izbor i stvarno uklanjanje starih algoritama.
- **Algoritam bira poruka.** Server koji veruje polju `alg` iz JWT tokena „agilan“ je na pogrešan način ([[Kod za autentifikaciju poruke]]). *Zaštita:* dozvoljeni algoritmi su fiksirani na serveru.
