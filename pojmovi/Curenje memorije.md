---
tip: pojam
aliases: [memory leak, Neoslobađanje alocirane memorije]
izvor: 'MITRE CWE-401, Missing Release of Memory after Effective Lifetime: https://cwe.mitre.org/data/definitions/401.html; SEI CERT C MEM31-C, Free dynamically allocated memory when no longer needed: https://cmu-sei.github.io/secure-coding-standards/sei-cert-c-coding-standard/rules/memory-management-mem/mem31-c/'
status: prihvaćeno
sloj: jezgro
---
# Curenje memorije (memory leak)

## Definicija
Curenje memorije nastaje kada program ne oslobodi dinamički alociranu memoriju nakon što mu više nije potrebna, zbog čega ona ostaje zauzeta i nije dostupna za ponovnu alokaciju i upotrebu.

## Primer
U modulu za generisanje PDF faktura u [[Fakturis]] funkcija po zahtevu alocira privremeni radni prostor na [[Heap|heap-u]]. Ako zahtev nema obavezna polja, funkcija zabeleži odbijanje i vrati se bez poziva `std::free(workspace)`. Pošto lokalni pokazivač prestaje da postoji povratkom iz funkcije, program više ne može da oslobodi tu alokaciju, iako memorija ostaje zauzeta. Napadač može da šalje veliki broj takvih zahteva i izazove ponavljanje greške, čime postepeno iscrpljuje memorijske resurse procesa.

```cpp
void generate_pdf(const Request& request) {
    auto* workspace =
        static_cast<char*>(std::malloc(PDF_WORKSPACE_SIZE));

    if (workspace == nullptr) {
        return;
    }

    if (!has_required_fields(request)) {
        log_rejection(request);
        return; // memorija nije oslobođena
    }

    build_pdf(request, workspace);
    std::free(workspace);
}
```

Kontraprimer: ako bi funkcija oslobodila `workspace` pre povratka i zatim ga ipak koristila, to je [[Korišćenje posle oslobađanja]], suprotna greška: memorija je oslobođena prerano, a ne nikad.

## Napomene
- Curenje memorije nije samo po sebi [[Memorijska ranjivost]]: ne podrazumeva neispravan pristup izvan granica [[Memorijski objekat|memorijskog objekta]] niti pristup memorijskom objektu nakon isteka njegovog životnog veka. Ako napadač može da izazove ponavljanje curenja, potrošnja memorije može da naraste do iscrpljivanja resursa i [[Narušavanje dostupnosti resursa|narušavanja dostupnosti]].
- MITRE CWE-401 koristi *memory leak* kao uobičajen naziv za neoslobađanje memorije, ali upozorava da se isti izraz koristi i za otkrivanje osetljivog sadržaja memorije. U ovoj belešci termin označava isključivo neoslobađanje alocirane memorije.
- Nastaje pri [[Ručno upravljanje memorijom|ručnom upravljanju memorijom]], gde programer određuje kada se memorija oslobađa.
- Nije svaka alokacija koja ostane zauzeta do završetka procesa curenje memorije. Memorija može namerno da se zadrži tokom celog životnog veka programa, ili vlasništvo nad njom može biti preneto drugom delu programa.
