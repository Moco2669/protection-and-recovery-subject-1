---
tip: pojam
aliases: [memory safety, memorijska bezbednost, memorijska sigurnost, bezbednost memorije]
izvor: 'RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajdovi 157 do 164; Hicks (UMD), Memory safety, preko materijala za kurs; Payer, CS527 Software Security; Szekeres, Payer, Wei, Song, SoK: Eternal War in Memory, IEEE S&P 2013: https://www.ieee-security.org/TC/SP2013/papers/4977a048.pdf; MITRE CWE-415, Double Free: https://cwe.mitre.org/data/definitions/415.html; MITRE CWE-672, Operation on a Resource after Expiration or Release: https://cwe.mitre.org/data/definitions/672.html'
status: prihvaćeno
sloj: temelj
---
# Bezbednost pristupa memoriji (memory safety)

## Definicija
Bezbednost pristupa memoriji je svojstvo izvršavanja programa u kome se memoriji pristupa samo preko pokazivača izvedenih iz adrese postojećeg [[Memorijski objekat|memorijskog objekta]] ili alokacije, unutar granica objekta i tokom njegovog životnog veka; čitaju se samo vrednosti prethodno postavljene inicijalizacijom ili upisom, a ista memorijska alokacija ne oslobađa se više od jednom.

## Primer
Dok modul za generisanje PDF faktura u [[Softverski proizvod|softverskom proizvodu]] firme [[Fakturis]] upisuje naziv kupca u [[Bafer|bafer]] od 64 bajta, ne prelazi njegov kraj, a bafer nije oslobođen, pristup memoriji je bezbedan. Upis 65. bajta narušava prostornu bezbednost, a čitanje bafera posle oslobađanja vremensku.

## Napomene
- Prostorna bezbednost je uslov da se pristupa samo unutar granica memorijskog objekta. Vremenska je uslov da se memorijskom objektu pristupa dok postoji, da se čitaju samo vrednosti prethodno postavljene inicijalizacijom ili upisom i da se alokacija oslobađa najviše jednom.
- Pokazivač ne mora da sadrži početnu adresu memorijskog objekta: može nastati iz adrese memorijskog objekta ili alokacije, na primer pomeranjem pokazivača unutar njihovih granica.
- Predavanje RBS 07 svrstava pristup preko neinicijalizovanog pokazivača i čitanje neinicijalizovanih podataka u vremenske greške. Ova baza ih razdvaja: [[Čitanje neinicijalizovane memorije]] odnosi se na čitanje nepostavljene vrednosti, dok klasifikacija neinicijalizovanog pokazivača ostaje otvorena. Izvori neinicijalizovani pokazivač klasifikuju različito. Isto važi za NULL i proizvedene pokazivače: kršenje uslova validnog porekla trenutno nema svoju klasu.
- Granica memorijskog objekta odnosi se na konkretan objekat ili podobjekat kome pokazivač pripada, a ne nužno na ceo objekat koji ga sadrži. Na primer, ako struktura sadrži niz `name[64]` i odmah iza njega pokazivač na funkciju, upis iza poslednjeg elementa niza izlazi iz granica niza čak i kada zahvata susedno polje iste strukture.
- Program ima bezbedan pristup memoriji ako je pristup memoriji bezbedan u svakom njegovom izvršavanju.
- Program sa bezbednim pristupom memoriji može imati druge ranjivosti, na primer SQL injekciju.
- Beleška popunjava pojam koji [[Aplikativni softver]] i [[Nativni kod]] samo nagoveštavaju.
