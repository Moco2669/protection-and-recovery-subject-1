---
tip: pojam
aliases: [lack of network segmentation, flat network, ravna mreža]
izvor: NIST SP 800-53 Rev. 5, SC-7 Boundary Protection; srodno: CWE-653 Improper Isolation or Compartmentalization
status: predlog
sloj: jezgro
---
# Nedostatak segmentacije mreže (lack of network segmentation)

## Definicija
Nedostatak segmentacije mreže je [[Ranjivost|ranjivost]] [[Interna mreža|interne mreže]] u kojoj su komponente različite namene i različitog nivoa zaštite u istom segmentu, pa svaki uređaj povezan na mrežu može direktno da komunicira sa svakim drugim.

## Primer
U internoj mreži firme [[Fakturis]] poslovni računari, aplikacioni server, NAS, GitLab, server za rezervne kopije i Wi-Fi za posetioce nalaze se u istom segmentu. Sa Jeleninog laptopa, kome za rad trebaju samo internet, administratorski deo aplikacije i deljeni folder, može se pristupiti i portu baze podataka i administratorskom interfejsu servera za rezervne kopije. Posetilac u sali za sastanke, sa lozinkom za Wi-Fi sa table, nalazi se u istoj mreži kao i serveri.

## Napomene
- Ova ranjivost sama ne otvara ulaz u sistem, ali napadaču koji je preuzeo jednu komponentu omogućava da se kreće ka drugim (lateral movement). U [[Napad|napadu]] ransomware grupe ona vodi od Jeleninog laptopa do skladišta dokumenata i rezervnih kopija.
