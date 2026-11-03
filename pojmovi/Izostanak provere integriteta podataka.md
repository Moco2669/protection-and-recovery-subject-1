---
tip: pojam
aliases: ["missing integrity check"]
izvor: "NIST SP 800-53 Rev. 5, SI-7 Software, Firmware, and Information Integrity, osnova za opis nedostatka provere, https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final; za prenos: MITRE CWE-353 Missing Support for Integrity Check, https://cwe.mitre.org/data/definitions/353.html"
---

# Izostanak provere integriteta podataka (missing integrity check)

## Definicija

Izostanak provere integriteta podataka je [[Slabost|slabost]] pri kojoj komponenta koristi prenete ili sačuvane podatke bez potrebne provere da nisu neovlašćeno izmenjeni nakon pouzdane tačke njihovog nastanka ili čuvanja.

## Primer

Digitalni poslovni dokument nastaje u pouzdanoj obradi, čuva se i kasnije ponovo koristi. Pretpostavimo da napadač može izmeniti njegov sadržaj, a da komponenta pri korišćenju ne proverava potrebni dokaz da sadržaj nije neovlašćeno promenjen. Ako izmenjenu verziju prihvati kao original, nedostatak provere omogućava da narušavanje integriteta ostane neotkriveno. Način provere zavisi od vrste skladišta ili prenosa i zahteva zaštite podataka.

## Napomene

Definicija ne zahteva određenu bazu, datotečni format ni mrežni protokol. Provera konkretizuje kako se utvrđuje integritet pri prijemu ili kasnijem korišćenju.

Provera obične kontrolne sume nije dovoljna ako napadač može izmeniti i podatak i očekivanu sumu. Očekivana vrednost ili drugi dokaz moraju imati pouzdano poreklo.

Dozvoljena poslovna izmena nije sama po sebi narušavanje integriteta. Pitanje je da li promena odgovara pravilima i može li se nedozvoljena promena otkriti.

Ovaj nedostatak ne objašnjava kako je napadač stekao pravo izmene. To može biti druga ranjivost; provera integriteta i [[Neispravna kontrola pristupa|kontrola pristupa]] imaju različite uloge.
