---
tip: pojam
aliases: ["weakness"]
izvor: "MITRE CWE Glossary, Weakness, Class Weakness i Vulnerability, https://cwe.mitre.org/documents/glossary/; za širi obuhvat komponenti: NIST CSRC Glossary, vulnerability, https://csrc.nist.gov/glossary/term/vulnerability"
---

# Slabost (weakness)

## Definicija

Slabost je vrsta nedostatka u projektovanju, izradi, podešavanju ili upotrebi komponente sistema, čije konkretne pojave u odgovarajućim uslovima mogu predstavljati ranjivosti koje omogućavaju radnje suprotne bezbednosnim zahtevima.

## Primer

U sistemu organizacije podrška sme da čita poslovni dokument, ali ne i da ga menja. Ako komponenta koja obrađuje zahtev proverava samo prijavu, pa izvrši i zahtev podrške za izmenu tog dokumenta, u toj komponenti postoji konkretna ranjivost. Vrsta nedostatka je [[Neispravna kontrola pristupa|neispravna kontrola pristupa]], zahtev ograničava ko sme da menja dokument, a pretnja po komponenti je neovlašćena izmena podataka tokom obrade. Primer ne zavisi od namene dokumenta, vrste proizvoda ili izabrane baze.

## Napomene

Slabost označava vrstu nedostatka, a ranjivost njegovu konkretnu pojavu u komponenti koja u datim uslovima omogućava radnju suprotnu bezbednosnom zahtevu. Jedna vrsta slabosti može imati više konkretnih pojava, a jedna ranjivost može zavisiti od više povezanih nedostataka.

Pretnja po komponenti opisuje moguće narušavanje svojstva resursa u određenoj komponenti. Napad je niz radnji kojim napadač pokušava da je ostvari.

Nedostatak može postojati i u postupku ljudske komponente. Za utvrđivanje konkretne ranjivosti potrebno je pokazati koje nedozvoljeno postupanje taj nedostatak omogućava.

Postojanje ranjivosti ne znači da je napad već izveden.
