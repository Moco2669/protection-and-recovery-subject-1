---
tip: pojam
aliases: [machine code injection, injekcija koda, code injection, ubacivanje koda]
izvor: 'RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajdovi 97 do 123; McCamant, CSci 4271W, Day 6: Memory safety attacks 2, University of Minnesota (2022): https://classpages.cselabs.umn.edu/Spring-2022/csci4271/slides/05-mem-attacks-2-8up.pdf; Aleph One, Smashing The Stack For Fun And Profit, Phrack 49 (1996): https://phrack.org/issues/49/smashing-the-stack-for-fun-and-profit'
status: prihvaćeno
sloj: jezgro
---
# Injekcija mašinskog koda (machine code injection)

## Definicija
Injekcija mašinskog koda je [[Preuzimanje toka izvršavanja|preuzimanje toka izvršavanja]] u kome napadač smešta sopstvene mašinske instrukcije u memoriju procesa i preusmerava izvršavanje na njih.

## Primer
Modul za generisanje PDF faktura u [[Fakturis]] kopira naziv kupca iz zahteva u lokalni [[Bafer|bafer]] od 64 bajta. Napadač pošalje naziv od 200 bajtova: početni deo sadrži mašinske instrukcije, a deo koji prepisuje sačuvanu povratnu adresu sadrži adresu bafera. Kada funkcija završi, program prelazi na instrukcije u baferu i izvršava ih.

Kontraprimer: ako napadač sačuvanu povratnu adresu preusmeri na postojeću funkciju `system` u biblioteci, to je [[Ponovna upotreba koda]], jer se izvršavaju već postojeće instrukcije.

## Napomene
- Ubačene instrukcije nazivaju se shellcode. Naziv potiče od primera u kome instrukcije pokreću shell, ali shellcode može da obavlja i drugu zlonamernu funkcionalnost.
- Klasičan oblik je napad poznat kao stack smashing: napadač smešta instrukcije u lokalni bafer na [[Stek|steku]], a zatim prekoračenjem bafera prepisuje sačuvanu povratnu adresu tako da pokazuje na taj bafer.
- Kada napadač ne zna tačnu adresu bafera, može ispred shellcode-a da postavi niz NOP instrukcija (NOP sled). Tada je dovoljno da preusmerena adresa pogodi bilo koju instrukciju u tom nizu.
- Ako se instrukcije unose kroz funkciju koja obrađuje nul-terminisane C niske, nul-bajt može prerano da prekine kopiranje. Zato takav shellcode mora biti kodiran bez nul-bajtova. Ovo ograničenje ne važi za svaki način prenosa ili kopiranja podataka.
- Klasična izvedba zahteva da napadač može da upiše instrukcije u memorijsku oblast i da se ona kasnije izvršava. W⊕X sprečava da stranica bude istovremeno upisiva i izvršna, dok [[Sprečavanje izvršavanja podataka|DEP]] koristi hardversku podršku NX/XD da označi odabrane memorijske stranice kao neizvršive. To otežava neposredno izvršavanje shellcode-a; ako proces dopušta promenu dozvola stranice, napadač može pokušati da je učini izvršivom.
- [[Randomizacija rasporeda adresnog prostora|ASLR]] može otežati pronalaženje adrese bafera sa ubačenim instrukcijama, naročito kada se bafer nalazi u randomizovanoj oblasti kao što je stek ili heap. Ne sprečava upis instrukcija niti njihovo izvršavanje ako napadač sazna odgovarajuću adresu.
- Alias `code injection` ovde označava ubacivanje mašinskih instrukcija. Ne treba ga poistovećivati sa CWE-94, koji opisuje generisanje sintakse koda pod uticajem spoljnog ulaza.
