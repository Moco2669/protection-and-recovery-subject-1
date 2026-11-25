---
tip: pojam
aliases: [memory safety vulnerability]
izvor: 'RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajdovi 152 i 159 do 161; MITRE CWE-1399, Comprehensive Categorization: Memory Safety (kategorija, ne služi za mapiranje stvarnih ranjivosti): https://cwe.mitre.org/data/definitions/1399.html'
status: prihvaćeno
sloj: jezgro
---
# Memorijska ranjivost (memory safety vulnerability)

## Definicija
Memorijska ranjivost je ranjivost programa zbog koje ulaz koji napadač kontroliše može da naruši [[Memorijska bezbednost|memorijsku bezbednost]] tog programa.

## Primer
Modul za generisanje PDF faktura u [[Softverski proizvod|softverskom proizvodu]] firme [[Fakturis]] kopira naziv kupca iz zahteva u [[Bafer|bafer]] od 64 bajta bez provere dužine. Naziv od 200 bajtova upiše 136 bajtova preko susedne memorije, što je memorijska ranjivost.

Kontraprimer: ako modul odbija nazive duže od 64 bajta, ranjivosti nema. SQL injekcija u istom proizvodu je ranjivost, ali nije memorijska.

## Napomene
- Iskorišćava je [[Napad iskorišćavanjem memorijske ranjivosti]].
- Narušavanje memorijske bezbednosti koje napadač ne može da izazove je programska greška, a ne ranjivost u ovom smislu.
- Podvrste slede iz narušenog uslova memorijske bezbednosti: [[Prostorna memorijska ranjivost|prostorne]] (pristup van granica objekta) i [[Vremenska memorijska ranjivost|vremenske]] (pristup pre inicijalizacije ili nakon isteka životnog veka objekta, odnosno ponovno oslobađanje već oslobođene memorije).
- [[Curenje memorije]] nije memorijska ranjivost: samo po sebi ne narušava prostornu ni vremensku memorijsku bezbednost, ali ponovljeno izazivanje može iscrpeti memorijske resurse i dovesti do [[Narušavanje dostupnosti resursa|narušavanja dostupnosti resursa]]. Celobrojno prekoračenje takođe nije samo po sebi memorijska ranjivost, ali može dovesti do nje ako izazove neispravan pristup memoriji.
