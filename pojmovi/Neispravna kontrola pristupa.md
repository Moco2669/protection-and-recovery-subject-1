---
tip: pojam
aliases: ["improper access control", "broken access control"]
izvor: "MITRE CWE-284: Improper Access Control, https://cwe.mitre.org/data/definitions/284.html"
---

# Neispravna kontrola pristupa (improper access control)

## Definicija

Neispravna kontrola pristupa je [[Slabost|slabost]] pri kojoj komponenta ne ograničava ili pogrešno ograničava radnje učesnika nad resursom, pa omogućava pristup ili radnju suprotnu pravilima dozvoljenog korišćenja tog resursa.

## Primer

U sistemu organizacije podrška sme da čita poslovni dokument, dok izmenu sme da zatraži samo izričito ovlašćeni korisnik. Ako komponenta prihvati prijavu podrške, ali pri obradi zahteva ne ograniči izmenu prema tom pravilu, izvršiće nedozvoljenu radnju. Konkretna ranjivost je takvo sprovođenje pristupa u određenoj komponenti; pretnja po njoj je narušavanje integriteta dokumenta. Isti tip nedostatka može se ispitivati pri obradi zahteva ili neposrednom pristupu skladištu.

## Napomene

Uspešna prijava ne daje pravo na svaku radnju. Razrada pravila pripada [[Kontrola pristupa|kontroli pristupa]]; prava ne moraju biti zasnovana samo na ulozi.

Provera se odnosi i na radnju i na konkretan resurs, ne samo na dostupnost dugmeta.

Nepotrebno dodeljeno pravo i izostala provera prava nisu isti nedostatak: određivanje obima prava i sprovođenje provere dva su različita pitanja. Mogu se javiti zajedno, ali jedno ne podrazumeva drugo. Oba nedostatka obuhvaćena su ovim opštijim pojmom.

Neispravna kontrola može se pojaviti pri obradi, pri pristupu skladištu ili pri prosleđivanju podataka. Ove celine nisu međusobno isključive vrste slabosti.
