---
tip: pojam
aliases: [Čitanje neinicijalizovane memorije, uninitialized memory read, read of uninitialized memory]
izvor: 'SEI CERT C EXP33-C, Do not read uninitialized memory: https://cmu-sei.github.io/secure-coding-standards/sei-cert-c-coding-standard/rules/expressions-exp/exp33-c/; MITRE CWE-457, Use of Uninitialized Variable: https://cwe.mitre.org/data/definitions/457.html; RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), slajd 163'
status: prihvaćeno
sloj: jezgro
---
# Čitanje neinicijalizovane memorije (uninitialized memory read)

## Definicija
Čitanje neinicijalizovane memorije je [[Vremenska memorijska ranjivost]] u kojoj ulaz koji napadač kontroliše može da navede program da pročita vrednost memorijskog objekta pre nego što je ta vrednost određena inicijalizacijom ili prethodnim upisom.

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

Kada zahtev ne sadrži podatak o broju stranica, promenljiva `page_count` ostaje neinicijalizovana, ali se njena vrednost ipak koristi prilikom generisanja PDF-a.
