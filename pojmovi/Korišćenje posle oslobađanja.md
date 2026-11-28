---
tip: pojam
aliases: [use after free, UAF]
izvor: 'MITRE CWE-416, Use After Free: https://cwe.mitre.org/data/definitions/416.html; MITRE CWE-825, Expired Pointer Dereference: https://cwe.mitre.org/data/definitions/825.html; RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajdovi 131, 132 i 160; Szekeres, Payer, Wei, Song, SoK: Eternal War in Memory, IEEE S&P 2013: https://www.ieee-security.org/TC/SP2013/papers/4977a048.pdf'
status: prihvaćeno
sloj: jezgro
---
# Korišćenje posle oslobađanja (use after free)

## Definicija
Korišćenje posle oslobađanja je [[Vremenska memorijska ranjivost|vremenska memorijska ranjivost]] zbog koje program može da pročita ili upiše memoriju preko pokazivača pošto je ta memorija oslobođena.

## Primer
Modul za generisanje PDF faktura u [[Fakturis]] zauzme zapis o fakturi koji sadrži i pokazivač na funkciju za formatiranje iznosa. Zapis se oslobodi kad zahtev bude odbijen, ali ga modul kasnije ipak koristi da pozove tu funkciju. U međuvremenu je zahtev koji je napadač poslao dobio istu memoriju i upisao adresu koju je izabrao, pa modul izvršava kod na toj adresi.

Kontraprimer: ako modul samo drugi put pozove oslobađanje iste alokacije, to je [[Dvostruko oslobađanje]].

## Napomene
- Oslobođena memorija može biti ponovo dodeljena i sačuvana u drugom pokazivaču, dok stari pokazivač ukazuje unutar nove alokacije. Zato upis menja tuđe podatke, a čitanje ih otkriva.
- CWE navodi izmenu memorije, curenje informacija pri čitanju i izvršavanje neovlašćenog koda kao posledice.
- Pokazivač koji ukazuje na oslobođenu memoriju zove se viseći pokazivač (dangling pointer). CWE taj termin navodi kao alternativni naziv, ali je on stanje pokazivača, a greška je njegovo korišćenje.
- CWE-416 je poseban slučaj šireg CWE-825 (Expired Pointer Dereference).
- Nastaje pri [[Ručno upravljanje memorijom|ručnom upravljanju memorijom]], a CWE kao jednu od mera navodi jezik sa automatskim upravljanjem memorijom.
