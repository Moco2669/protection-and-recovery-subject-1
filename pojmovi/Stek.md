---
tip: pojam
aliases: [stack, call stack]
izvor: 'RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajdovi 15, 16 i 55 do 59; Cornell CS 3410, The Stack, The Heap, the Dynamic Memory Allocation: https://www.cs.cornell.edu/courses/cs3410/2026sp/notes/mem.html'
status: prihvaćeno
sloj: temelj
---
# Stek (stack)

## Definicija
Stek je deo memorije procesa u kome se za svaki poziv funkcije zauzima prostor (stek okvir) za njene lokalne promenljive i povratnu adresu, pri čemu se taj prostor oslobađa čim funkcija završi.

## Primer
Funkcija modula za generisanje PDF faktura u [[Fakturis]] ima lokalni [[Bafer|bafer]] od 64 bajta za naziv kupca. Dok funkcija traje, bafer je na steku, a čim se vrati, nestaje.

Kontraprimer: bafer zauzet pozivom `malloc` nije na steku, već na [[Heap|heap-u]].

## Napomene
- Povratna adresa je adresa instrukcije na koju program prelazi kad funkcija završi.
- Na x86 stek raste ka nižim adresama, a bafer se popunjava ka višim, pa [[Prekoračenje bafera|prekoračenje]] lokalnog bafera stiže do povratne adrese.
- U srpskim materijalima se koristi „Stek“ (na primer PMF Kragujevac).
