---
tip: pojam
aliases: [memory safety, bezbednost memorije]
izvor: 'RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajdovi 153 do 160; Hicks (UMD), Memory safety, preko materijala za kurs; Payer, CS527 Software Security; Szekeres, Payer, Wei, Song, SoK: Eternal War in Memory, IEEE S&P 2013: https://www.ieee-security.org/TC/SP2013/papers/4977a048.pdf; MITRE CWE-415, Double Free: https://cwe.mitre.org/data/definitions/415.html; MITRE CWE-672, Operation on a Resource after Expiration or Release: https://cwe.mitre.org/data/definitions/672.html'
status: prihvaćeno
sloj: temelj
---
# Memorijska bezbednost (memory safety)

## Definicija
Memorijska bezbednost je svojstvo izvršavanja programa da se svaki pristup memoriji vrši preko pokazivača koji ima validno poreklo, unutar granica objekta na koji ukazuje i dok taj objekat postoji; da se iz objekta čitaju samo vrednosti koje su u njega prethodno upisane; i da se nijedan memorijski objekat ne oslobađa više od jednom.

## Primer
Dok modul za generisanje PDF faktura u [[Softverski proizvod|softverskom proizvodu]] firme [[Fakturis]] upisuje naziv kupca u [[Bafer|bafer]] od 64 bajta, ne prelazi njegov kraj, a bafer nije oslobođen, izvršavanje je memorijski bezbedno. Upis 65. bajta narušava prostornu bezbednost, a čitanje bafera posle oslobađanja vremensku.

## Napomene
- Prostorna bezbednost je uslov da se pristupa samo unutar granica objekta. Vremenska je uslov da se objektu pristupa dok postoji, da se iz njega čitaju samo prethodno upisane vrednosti i da se objekat ne oslobađa više od jednom.
- Predavanje RBS 07 svrstava pristup preko neinicijalizovanog pokazivača i čitanje neinicijalizovanih podataka u vremenske greške. Ova baza ih razdvaja: [[Čitanje neinicijalizovane memorije]] odnosi se na čitanje nepostavljene vrednosti, dok klasifikacija neinicijalizovanog pokazivača ostaje otvorena. Izvori neinicijalizovani pokazivač klasifikuju različito.
- Program je memorijski bezbedan ako je svako njegovo izvršavanje memorijski bezbedno.
- Memorijski bezbedan program može imati druge ranjivosti, na primer SQL injekciju.
- Beleška popunjava pojam koji [[Aplikativni softver]] i [[Nativni kod]] samo nagoveštavaju.
