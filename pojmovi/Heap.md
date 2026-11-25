---
tip: pojam
aliases: [hip, dinamička memorija, hrpa]
izvor: 'RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajdovi 16 i 23; Cornell CS 3410, The Stack, The Heap, the Dynamic Memory Allocation: https://www.cs.cornell.edu/courses/cs3410/2026sp/notes/mem.html'
status: prihvaćeno
sloj: temelj
---
# Heap (heap)

## Definicija
Heap je deo memorije procesa u kome se delovi memorije zauzimaju i oslobađaju tokom izvršavanja programa, nezavisno od poziva funkcija.

## Primer
Modul za generisanje PDF faktura u [[Fakturis]] pozivom `malloc` zauzme [[Bafer|bafer]] za naziv kupca kad primi zahtev, a oslobodi ga kad obradi taj zahtev. Bafer je na heap-u i posle povratka iz funkcije koja ga je zauzela.

Kontraprimer: lokalna promenljiva funkcije nije na heap-u i nestaje kad funkcija završi.

## Napomene
- Definicija pokriva i heap sa automatskim oslobađanjem. U C/C++ programer eksplicitno zauzima i oslobađa memoriju na heap-u, a u [[Izvršno okruženje|izvršnom okruženju]] to radi okruženje, vidi [[Ručno upravljanje memorijom]].
- Heap nije struktura podataka istog imena (prioritetni red), već samo region memorije.
