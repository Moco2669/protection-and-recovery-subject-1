---
tip: pojam
aliases: [object, objekat]
izvor: 'ISO/IEC 9899:2011 (C11), odeljci 3.15 (object) i 6.2.4 (storage durations of objects), citirano u WG14 N2328: https://open-std.org/JTC1/SC22/WG14/www/docs/n2328.pdf; RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajd 158'
status: prihvaćeno
sloj: temelj
---
# Memorijski objekat (object)

## Definicija
Memorijski objekat je deo memorije određene veličine u kome program čuva vrednost, od trenutka kada se zauzme do trenutka kada se oslobodi.

## Primer
Bafer od 64 bajta za naziv kupca u modulu za generisanje PDF faktura u [[Fakturis]] je memorijski objekat. Granice su mu prvi i 64. bajt, a postoji dok funkcija koja ga je zauzela ne završi, odnosno do poziva `free` ako je na [[Heap|heap-u]].

Kontraprimer: slobodan deo memorije koji nije zauzet nije memorijski objekat. Pokazivač na bafer takođe nije bafer, već zaseban memorijski objekat koji čuva adresu.

## Napomene
- Veličina određuje granice objekta. Izlazak iz njih je [[Prostorna memorijska ranjivost|prostorna]] greška.
- Pristup van životnog veka objekta je [[Vremenska memorijska ranjivost|vremenska]] greška.
- U standardu C objekat je opštiji od instance klase: i obična promenljiva tipa `int` je objekat.
- Za granice se uzima objekat iz kog je pokazivač izveden, na primer niz unutar strukture, a ne cela struktura.
- Na pojmu počiva [[Bezbednost pristupa memoriji]].
