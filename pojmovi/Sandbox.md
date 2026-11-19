---
tip: pojam
aliases: [sandbox, application sandbox, sendboks]
izvor: 'NIST CSRC Glossary, sandbox: https://csrc.nist.gov/glossary/term/sandbox; Android Application Sandbox: https://source.android.com/docs/security/app-sandbox'
status: predlog
sloj: temelj
---
# Sandbox (sandbox)

## Definicija
Sandbox je ograničeno okruženje za izvršavanje aplikacije koje dozvoljava samo određene radnje i pristupe podacima, drugim programima i mogućnostima uređaja.

## Primer
Kada Jelena iz firme [[Fakturis]] na privatnom telefonu koristi aplikaciju za službenu e-poštu, operativni sistem ograničava njen pristup podacima drugih aplikacija. Pokretanje aplikacije ne daje joj pristup svim podacima i mogućnostima telefona.

## Napomene
- Sandbox ograničava šta aplikacija sme da uradi ostatku sistema. Deo je njenog [[Sistemsko okruženje|sistemskog okruženja]].
- Na Androidu operativni sistem sprovodi odvajanje aplikacija i proverava prava pristupa.
- Sandbox označava koncept ograničenog izvršavanja, ali i konkretno okruženje koje taj koncept sprovodi. Android Application Sandbox je primer stvarne realizacije; zato nije tačno reći da je sandbox samo koncept, a kontejner jedino konkretno rešenje.
- Sandbox i [[Kontejner|kontejner]] nisu sinonimi. Sandbox naglašava bezbednosnu namenu i dozvoljene radnje, dok kontejner označava izdvajanje izvršnog okruženja uz deljeno jezgro OS-a. Docker je primer konkretne tehnologije za kontejnere.
- Sandbox se može realizovati ograničenjima procesa u OS-u, korišćenjem kontejnera ili [[Virtuelna mašina|virtuelne mašine]], ili kombinacijom mehanizama. Može postojati i unutar tih okruženja.
- Postojanje sandboxa ne garantuje da nema ranjivosti.
