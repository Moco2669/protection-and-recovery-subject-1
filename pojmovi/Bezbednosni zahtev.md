---
tip: pojam
aliases: [security requirement]
izvor: NIST SP 800-53 Rev. 5, Appendix A Glossary, "security requirement" (FIPS 200, adapted)
status: predavanje
sloj: temelj
---
# Bezbednosni zahtev (security requirement)

## Definicija
Bezbednosni zahtev je pravilo koje za određeni [[Resurs|resurs]] utvrđuje ko sme, a ko mora moći da izvrši koje radnje nad njim. Svaki bezbednosni zahtev konkretizuje neko [[Bezbednosno svojstvo|bezbednosno svojstvo]] tog resursa.

## Primer
Za fakture u aplikaciji [[Fakturis]] važe, između ostalih, ovi zahtevi:
- fakturu vide samo korisnik koji ju je izdao i kupac kome je upućena (poverljivost);
- status „plaćeno“ postavlja samo potvrđeno obaveštenje PayNet-a (integritet);
- korisnik mora moći da izda fakturu u svako doba, posebno poslednjih dana u mesecu (dostupnost).

Kontraprimer: „Aplikacija proverava potpis svakog obaveštenja PayNet-a.“ Ova rečenica kaže kako se nešto postiže, a ne šta mora da važi. To je [[Bezbednosna kontrola|bezbednosna kontrola]], a ne zahtev.

## Napomene
- Potpun pregled zahteva za Fakturis, po resursima i svojstvima, nalazi se u beleški konteksta, odeljak *Bezbednosni zahtevi*.
- [[Ranjivost]] se uvek određuje u odnosu na neki zahtev: komponenta je ranjiva ako omogućava radnju suprotnu zahtevu.
