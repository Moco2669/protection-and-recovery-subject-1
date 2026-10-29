---
tip: pojam
aliases: [component-level threat]
izvor: ZOSS 03 (predavanje); srodno: STRIDE po elementu, A. Shostack, Threat Modeling: Designing for Security, Wiley, 2014
status: predavanje
sloj: temelj
---
# Pretnja po komponenti (component-level threat)

## Definicija
Pretnja po komponenti je [[Pretnja|pretnja]] ograničena na jednu [[Komponenta sistema|komponentu sistema]] u kojoj se ugroženi [[Resurs|resurs]] nalazi.

## Primer
Pretnja „kriminalna grupa narušava poverljivost faktura“ u firmi [[Fakturis]] razlaže se na pet pretnji po komponenti, jer se fakture nalaze u web aplikaciji, bazi podataka, skladištu dokumenata (PDF), na serveru za rezervne kopije i u testnom okruženju, koje koristi kopiju produkcione baze.

Kontraprimer: GitLab repozitorijum ne sadrži fakture. Napadač ga možda koristi da pronađe API ključ ili lozinku baze, ali za ovu pretnju GitLab nije komponenta u kojoj se ugroženi resurs nalazi, pa tu nema pretnje po komponenti.

## Napomene
- Razlaganje pokazuje da zaštita samo jedne komponente ne štiti resurs. Ako aplikacija ispravno proverava prava pristupa, fakture su i dalje izložene kroz testno okruženje i rezervne kopije.
