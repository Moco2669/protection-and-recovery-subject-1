---
tip: pojam
aliases: [manual memory management, ručna kontrola memorije]
izvor: 'The Rust Programming Language, What Is Ownership?: https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html'
status: predlog
sloj: temelj
---
# Ručno upravljanje memorijom (manual memory management)

## Definicija
Ručno upravljanje memorijom je način rada u kojem programer u kodu određuje kada se zauzima memorija za podatke i kada se ona oslobađa za ponovnu upotrebu.

## Primer
Ako bi deo [[Softverski proizvod|softverskog proizvoda]] firme [[Fakturis]] bio napisan u C-u, programer bi mogao da zauzme memoriju za stavke fakture i oslobodi je kada obrada završi. Ovo je ilustrativna mogućnost, a ne utvrđena tehnologija firme.

## Napomene
- Programer mora voditi računa da se memorija ne koristi nakon oslobađanja i da se ne oslobađa više puta.
- Ako se nepotrebna zauzeta memorija ne oslobađa, program vremenom može trošiti sve više memorije.
- Greške u korišćenju memorije mogu izazvati pad programa ili omogućiti napadaču da promeni njegovo ponašanje.
- Nije sinonim za [[Nativni kod|nativni kod]]. Program može biti preveden u nativni kod i koristiti drugačiji model upravljanja memorijom.
- U C++ programer može koristiti objekte koji oslobađaju memoriju po završetku svog životnog veka, umesto da svako oslobađanje piše kao zasebnu naredbu.
