---
tip: pojam
aliases: [memory corruption attack, memory exploitation, napad na memoriju, iskorišćavanje memorijske ranjivosti]
izvor: 'Szekeres, Payer, Wei, Song, SoK: Eternal War in Memory, IEEE S&P 2013: https://www.ieee-security.org/TC/SP2013/papers/4977a048.pdf; RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajdovi 61, 124 i 152; MITRE CAPEC-123, Buffer Manipulation: https://capec.mitre.org/data/definitions/123.html'
status: prihvaćeno
sloj: jezgro
---
# Napad iskorišćavanjem memorijske ranjivosti (memory corruption attack)

## Definicija
Napad iskorišćavanjem memorijske ranjivosti je napad u kome napadač pripremljenim ulazom pokušava da izazove narušavanje [[Memorijska bezbednost|memorijske bezbednosti]] programa i time stekne mogućnost da promeni njegovo ponašanje ili pročita njegovu memoriju.

## Primer
Napadač pošalje zahtev za izdavanje fakture sa pažljivo sastavljenim nazivom kupca od 200 bajtova. Modul za generisanje PDF faktura u [[Fakturis]] ga kopira u [[Bafer|bafer]] od 64 bajta, pa [[Prekoračenje bafera|prekoračenje]] prepiše susedno polje sa statusom fakture i postavi ga na „plaćeno“. Napadač nema ovlašćenje da menja status, a ovako je stekao tu mogućnost.

Kontraprimer: SQL injekcija ne narušava memorijsku bezbednost programa, pa nije napad ovog tipa.

## Napomene
- Napad obično počinje izazivanjem memorijske greške, koja napadaču daje čitanje ili upis tamo gde ne bi smeo. Greška je [[Memorijska ranjivost]].
- Konkretno pripremljeno sredstvo kojim se ranjivost iskorišćava može biti [[Eksploit]]; napad obuhvata širi niz radnji, uključujući njegovu primenu.
- Ishodi su: [[Preuzimanje toka izvršavanja|preuzimanje toka izvršavanja]] (napadač određuje koji se kod izvršava; u procesu sa većim pravima vodi ka [[Dobijanje prevelikih privilegija]]), izmena podataka ([[Narušavanje integriteta podataka]]), otkrivanje sadržaja memorije ([[Narušavanje poverljivosti podataka]]) i rušenje programa ([[Narušavanje dostupnosti resursa]]).
- Otkrivanje sadržaja memorije je često samo korak ka drugom ishodu, na primer da bi se saznale adrese.
- Memorijsko iskorišćavanje je obično jedan korak u dužem napadu. Ono što sledi posle preuzimanja toka je zasebna tema.
- CAPEC ove napade vodi kao manipulaciju baferima (CAPEC-123).
