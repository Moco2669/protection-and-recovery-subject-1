---
tip: pojam
aliases: [stack canary, stack canary protection]
izvor: 'RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), PDF strane 175–178 (slajdovi 180–183); GCC, Instrumentation Options, -fstack-protector: https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html; Microsoft Learn, /GS (Buffer Security Check): https://learn.microsoft.com/en-us/cpp/build/reference/gs-buffer-security-check'
status: prihvaćeno
---
# Zaštita steka kanarincem (stack canary protection)

## Definicija
Zaštita steka kanarincem je [[Tehnička kontrola]] koja u okvir steka funkcije smešta posebnu zaštitnu vrednost između lokalnih bafera i podataka koji utiču na povratak iz funkcije, a pre povratka proverava da li je ta vrednost nepromenjena. Ako je vrednost promenjena, izvršavanje programa se prekida.

## Primer
U modulu za generisanje PDF faktura u [[Fakturis]], funkcija kopira naziv kupca u lokalni [[Bafer|bafer]] od 64 bajta. Funkcija je obuhvaćena kompajlerskom zaštitom steka kanarincem. Napadač pošalje naziv od 200 bajtova. Upis prekoračuje bafer i dopire do kanarinca, menjajući njegovu vrednost. Pre povratka iz funkcije provera otkriva promenu i prekida izvršavanje programa, umesto da dozvoli povratak preko potencijalno prepisane povratne adrese.

## Napomene
- Kontrola je tehnička jer je sprovode instrukcije koje kompajler dodaje programu. Primeri implementacije su GCC opcije `-fstack-protector` i `-fstack-protector-strong`, odnosno Microsoft opcija `/GS`.
- Provera otkriva određena oštećenja steka tek kada funkcija završava rad. Prekid izvršavanja sprečava nastavak kroz potencijalno oštećene upravljačke podatke, ali se prekoračenje bafera već dogodilo.
- Kompajler ne mora da zaštiti svaku funkciju. Obuhvat zavisi od opcije i od toga da li funkcija sadrži objekte koje kompajler smatra ranjivim. `-fstack-protector-all` obuhvata sve funkcije; druge varijante biraju podskup.
- Kanarinac ne otkriva svako prekoračenje bafera. Na primer, prepisivanje drugih podataka u objektu ne mora da promeni zaštitnu vrednost. Ne štiti ni bafer na heap-u od samog prekoračenja.
- Predavanje RBS 07 prikazuje terminatorske, nasumične i nasumične XOR kanarince (PDF strana 178, slajd 183). To su varijante načina formiranja zaštitne vrednosti, a ne različite vrste ove kontrole.
- Kontrola ublažava posledice [[Prekoračenje bafera|prekoračenja bafera]] na steku i može otežati [[Preuzimanje toka izvršavanja]] kada napad zavisi od prepisivanja povratne adrese. Ne uklanja [[Memorijska ranjivost|memorijsku ranjivost]].
- [[Integritet toka izvršavanja|CFI]] deluje na drugom mestu: proverava dozvoljenost prenosa kontrole, dok kanarinac otkriva određena oštećenja steka pre povratka iz funkcije.
