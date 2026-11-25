---
tip: pojam
aliases: [uninitialized memory read, read of uninitialized memory, korišćenje neinicijalizovane memorije]
izvor: 'SEI CERT C EXP33-C, Do not read uninitialized memory: https://cmu-sei.github.io/secure-coding-standards/sei-cert-c-coding-standard/rules/expressions-exp/exp33-c/; MITRE CWE-457, Use of Uninitialized Variable: https://cwe.mitre.org/data/definitions/457.html; MITRE CWE-908, Use of Uninitialized Resource: https://cwe.mitre.org/data/definitions/908.html; RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajd 163'
status: prihvaćeno
sloj: jezgro
---
# Čitanje neinicijalizovane memorije (uninitialized memory read)

## Definicija
Čitanje neinicijalizovane memorije je [[Vremenska memorijska ranjivost]] zbog koje program može da pročita vrednost objekta koja nikada nije postavljena inicijalizacijom ni upisom.

## Primer
U modulu za generisanje PDF faktura u [[Fakturis]]:

```c
void pdf_generate(const Request* request) {
    int page_count;

    if (request_has_page_count(request)) {
        page_count = parse_page_count(request);
    }

    pdf_write_metadata(page_count);
}
```

Kada zahtev ne sadrži podatak o broju stranica, promenljiva `page_count` ostaje neinicijalizovana, ali se njena vrednost ipak koristi prilikom generisanja PDF-a. Vrednost je ostatak ranijeg sadržaja steka: može biti nasumičan broj stranica ili deo tuđeg podatka, koji se tada upisuje u PDF koji korisnik dobija.

Kontraprimer: ako je promenljiva deklarisana kao `int page_count = 1;`, vrednost je uvek postavljena, pa ranjivosti nema. Ako bi modul pročitao inicijalizovan bajt iza kraja bafera, to je [[Čitanje van granica bafera]].

## Napomene
- Pokazivač i objekat su ispravni i unutar granica, ali vrednost nikada nije postavljena. Zato ovo nije [[Čitanje van granica bafera]].
- Pročitana vrednost je obično ostatak ranije upotrebe memorije. Može otkriti tuđe podatke ([[Narušavanje poverljivosti podataka]]) ili dovesti do nepredvidivog ponašanja, uključujući rušenje programa.
- Odnosi se na vrednost objekta, a ne na neinicijalizovani pokazivač, čija je klasifikacija otvorena (vidi [[Memorijska bezbednost]]).
