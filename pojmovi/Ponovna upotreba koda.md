---
tip: pojam
aliases: [code reuse, code-reuse attack, napad ponovnom upotrebom koda]
izvor: 'Shacham, The Geometry of Innocent Flesh on the Bone: Return-into-libc without Function Calls (on the x86), CCS 2007: https://doi.org/10.1145/1315245.1315313; McCamant, CSci 4271W, Day 6: Memory safety attacks 2, University of Minnesota (2022): https://classpages.cselabs.umn.edu/Spring-2022/csci4271/slides/05-mem-attacks-2-8up.pdf; RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajd 123'
status: prihvaćeno
sloj: jezgro
---
# Ponovna upotreba koda (code reuse)

## Definicija
Ponovna upotreba koda je [[Preuzimanje toka izvršavanja|preuzimanje toka izvršavanja]] u kome napadač preusmerava izvršavanje na instrukcije koje već postoje u memoriji procesa i povezuje ih redosledom koji je izabrao.

## Primer
Napadač prepiše sačuvanu povratnu adresu funkcije modula za PDF fakture na adresu funkcije `system` iz biblioteke C, a na steku pripremi vrednosti potrebne da `system` dobije pokazivač na nisku `"/bin/sh"`. Kada funkcija modula završi, program ulazi u postojeću funkciju `system` i izvršava je sa pripremljenim argumentom. Napadač nije ubacio nijednu novu instrukciju.

Kontraprimer: ako napadač smešta sopstvene instrukcije u bafer i preusmerava izvršavanje na njih, to je [[Injekcija mašinskog koda]].

## Napomene
- Jedan od ranih oblika je return-into-libc: napadač preusmerava izvršavanje na postojeće funkcije biblioteke, kao što je `system`. Moguće je povezati više poziva pripremanjem odgovarajućih okvira na steku; napad zato nije nužno ograničen na jednu funkciju.
- ROP (return-oriented programming) koristi kratke nizove postojećih instrukcija koji se završavaju instrukcijom za povratak (gadgets). Napadač ih povezuje preko povratnih adresa na steku, bez potrebe da poziva cele funkcije. Shacham je pokazao da takvi nizovi na x86 mogu da omoguće proizvoljno izračunavanje.
- Ne zahteva memorijsku oblast koja je istovremeno upisiva i izvršna. Instrukcije se izvršavaju iz već postojećih izvršivih oblasti, pa [[Sprečavanje izvršavanja podataka|DEP]]/NX ne sprečava ovaj oblik napada. Ni pravilo W⊕X ne zabranjuje izvršavanje iz postojećih izvršivih stranica.
- [[Randomizacija rasporeda adresnog prostora|ASLR]] otežava pronalaženje adresa postojećih funkcija i gadget-a, ali ne sprečava njihovo izvršavanje ako napadač uspe da sazna njihove adrese.
- [[Integritet toka izvršavanja|CFI]] može da ograniči upotrebu postojećih instrukcija ako lanac zahteva nedozvoljene prenose kontrole. Za ROP je posebno važno da li zaštita proverava i povratke iz funkcija (backward-edge); Microsoft CFG prvenstveno proverava indirektne pozive (forward-edge).
