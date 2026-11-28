---
tip: pojam
aliases: [temporal memory safety vulnerability]
izvor: 'RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajdovi 159 i 160; Hicks (UMD), Memory safety, preko materijala za kurs: https://user.eng.umd.edu/~danadach/Security_Fall_24/05-memsafety_24.pdf; Payer, CS527 Software Security, Security policies: https://nebelwelt.net/teaching/18-527-SoftSec/slides/05-security_policies.pdf; Szekeres, Payer, Wei, Song, SoK: Eternal War in Memory, IEEE S&P 2013: https://www.ieee-security.org/TC/SP2013/papers/4977a048.pdf; MITRE CWE-672, Operation on a Resource after Expiration or Release: https://cwe.mitre.org/data/definitions/672.html; MITRE CWE-415, Double Free: https://cwe.mitre.org/data/definitions/415.html'
status: prihvaćeno
sloj: jezgro
---
# Vremenska memorijska ranjivost (temporal memory safety vulnerability)

## Definicija
Vremenska memorijska ranjivost je [[Memorijska ranjivost|memorijska ranjivost]] zbog koje program može da izvrši operaciju nad [[Memorijski objekat|memorijskim objektom]] u trenutku kada objekat nije u stanju koje ta operacija zahteva: vrednost mora biti inicijalizovana da bi se čitala, a objekat mora još postojati da bi se čitao, upisivao ili oslobodio.

## Primer
Modul za generisanje PDF faktura u [[Fakturis]] oslobodi [[Bafer|bafer]] sa nazivom kupca kad zahtev bude odbijen, a zatim ga ipak upiše u PDF. Ako je ista memorija u međuvremenu dodeljena drugom zahtevu, PDF dobija njegove podatke.

## Napomene
- Stanje memorijskog objekta određuje koje su operacije dozvoljene. Vrednost može da se čita tek nakon inicijalizacije; čitanje i upis nisu dozvoljeni nakon prestanka životnog veka memorijskog objekta, a dinamička alokacija može da se oslobodi samo jednom. Kod lokalnog objekta životni vek se završava, na primer, povratkom iz funkcije, iako nije eksplicitno oslobođen pozivom `free`.
- Korišćenje posle oslobađanja i dvostruko oslobađanje nisu ista operacija. Prvo podrazumeva čitanje ili upis preko pokazivača nakon oslobađanja; drugo ponavljanje same operacije oslobađanja. MITRE CWE-672 opisuje širu klasu operacija nad resursom nakon isteka ili oslobađanja, a među demonstrativnim primerima navodi i dvostruko oslobađanje. U jednom od CWE hijerarhijskih prikaza CWE-415 je podvrsta CWE-672 i vodi se odvojeno od CWE-416 (Use After Free).
- Klase se u praksi mogu preklapati, pa vrstu određuje uslov bezbednosti pristupa memoriji koji je prekršen. Pristup iza kraja bafera je [[Prostorna memorijska ranjivost|prostorna]] ranjivost; pristup oslobođenom baferu, [[Čitanje neinicijalizovane memorije|čitanje neinicijalizovane vrednosti]] i ponovljeno oslobađanje pripadaju vremenskoj klasi.
- Vrste: [[Korišćenje posle oslobađanja]], [[Dvostruko oslobađanje]] i [[Čitanje neinicijalizovane memorije]].
