---
tip: pojam
aliases: [integrity]
izvor: ISO/IEC 27000:2018, 3.36 integrity; FIPS 199 (44 U.S.C. § 3552)
status: predavanje
sloj: temelj
---
# Integritet (integrity)

## Definicija
Integritet je [[Bezbednosno svojstvo|bezbednosno svojstvo]] [[Resurs|resursa]] da je tačan i potpun, i da nije izmenjen ni uništen na nedozvoljen način.

## Primer
Neko pošalje lažno obaveštenje o uplati na adresu `/api/paynet/obavestenje` aplikacije [[Fakturis]], i faktura od 120.000 dinara dobija status „plaćeno“, iako novac nije uplaćen. Niko nije video tuđe podatke, ali status fakture više ne odgovara stvarnosti, pa je integritet narušen.

Kontraprimer: korisnik stornira fakturu sa pogrešnim iznosom i izdaje novu, a aplikacija čuva obe uz oznaku storna. Izmena je dozvoljena i evidentirana, pa je integritet očuvan.
