---
tip: pojam
aliases: ["missing confidentiality protection in transit"]
izvor: "MITRE CWE-319: Cleartext Transmission of Sensitive Information, https://cwe.mitre.org/data/definitions/319.html; MITRE CWE-311: Missing Encryption of Sensitive Data, https://cwe.mitre.org/data/definitions/311.html"
---

# Izostanak zaštite poverljivosti prenosa (missing confidentiality protection in transit)

## Definicija

Izostanak zaštite poverljivosti prenosa je [[Slabost|slabost]] pri kojoj komponenta prenosi podatke čije je čitanje ograničeno bez zaštite potrebne da ih učesnik sa pristupom komunikacionom putu ne može neovlašćeno pročitati.

## Primer

Dve komponente razmenjuju poslovni dokument koji smeju da čitaju samo ovlašćeni učesnici. Ako sadržaj putuje čitljivo preko dela komunikacionog puta koji napadač može posmatrati, nedostatak zaštite tog prenosa predstavlja konkretnu ranjivost. Pretnja po prenosnoj komponenti je neovlašćeno otkrivanje podataka tokom prenosa. Protokol, namena dokumenta i tačne krajnje komponente određuju se tek pri daljoj konkretizaciji.

## Napomene

Poverljivost prenosa odnosi se na sprečavanje neovlašćenog čitanja podataka. [[Izostanak provere integriteta podataka]] odnosi se na neotkrivenu neovlašćenu izmenu. Ista kontrola može podržavati zaštitu oba svojstva.

Zaštita jedne veze ne dokazuje zaštitu svih drugih veza. Potrebna zaštita određuje se prema podacima, komunikacionom putu i mogućnostima neovlašćenog učesnika.
