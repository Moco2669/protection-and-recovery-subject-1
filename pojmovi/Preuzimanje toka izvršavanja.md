---
tip: pojam
aliases: [control-flow hijacking, control-flow attack, code redirection attack, otimanje toka izvršavanja]
izvor: 'Szekeres, Payer, Wei, Song, SoK: Eternal War in Memory, IEEE S&P 2013: https://www.ieee-security.org/TC/SP2013/papers/4977a048.pdf; Cornell CS 5431, Control Flow Integrity: https://www.cs.cornell.edu/courses/cs5431/2017sp/Lec2-CFI.pdf; RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajdovi 97 do 123'
status: prihvaćeno
sloj: jezgro
---
# Preuzimanje toka izvršavanja (control-flow hijacking)

## Definicija
Preuzimanje toka izvršavanja je [[Napad iskorišćavanjem memorijske ranjivosti|napad iskorišćavanjem memorijske ranjivosti]] u kome napadač menja adresu koda koji program treba da izvrši, na primer povratnu adresu funkcije ili pokazivač na funkciju, da bi program izvršavao kod koji je napadač izabrao.

## Primer
Funkcija modula za generisanje PDF faktura u [[Fakturis]] ima lokalni [[Bafer|bafer]] od 64 bajta, a iza njega na [[Stek|steku]] stoji povratna adresa. Napadač pošalje naziv od 200 bajtova čiji poslednji bajtovi sadrže adresu koju je izabrao. Kad funkcija završi, program umesto u pozivaoca prelazi na tu adresu i izvršava kod koji je napadač izabrao.

Kontraprimer: ako napadač samo prepiše polje sa statusom fakture, ne menja se koji se kod izvršava, to je izmena podataka.

## Napomene
- Kod koji se izvršava može biti ubačen ili već postojeći u programu.
- Prema poreklu instrukcija, razlikuju se [[Injekcija mašinskog koda]] i [[Ponovna upotreba koda]]. Ova podela opisuje tehniku, a ne međusobno isključive faze napada: napadač može, na primer, ponovnom upotrebom postojećeg koda da promeni dozvole memorijske oblasti, a zatim izvrši instrukcije koje je prethodno ubacio.
- Najčešća meta je povratna adresa na steku, a druge su pokazivači na funkcije, kao u primeru [[Korišćenje posle oslobađanja|korišćenja posle oslobađanja]].
- Napadač izvršava kod sa pravima procesa u kome program radi, što vodi ka [[Dobijanje prevelikih privilegija]] ako proces ima veća prava.
- [[Zaštita steka kanarincem]] može da prekine izvršavanje pre povratka iz funkcije ako napad prepiše zaštićenu vrednost na steku; ne štiti od svih načina preusmeravanja toka izvršavanja.
- [[Randomizacija rasporeda adresnog prostora|ASLR]] otežava napadaču da predvidi adresu na koju želi da preusmeri izvršavanje, ali ne sprečava samo prepisivanje povratne adrese niti garantuje da napad neće uspeti.
- [[Integritet toka izvršavanja|CFI]] proverava da li se prenosi kontrole uklapaju u dozvoljenu politiku i može da odbije nedozvoljeni cilj. Efekat zavisi od toga koje vrste prenosa kontrole konkretna implementacija proverava.
