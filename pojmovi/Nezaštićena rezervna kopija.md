---
tip: pojam
aliases: [unprotected backup, online backup]
izvor: NIST SP 800-53 Rev. 5, CP-9 System Backup; CISA, #StopRansomware Guide (izolovane, šifrovane rezervne kopije)
status: predlog
sloj: jezgro
---
# Nezaštićena rezervna kopija (unprotected backup)

## Definicija
Nezaštićena rezervna kopija je [[Ranjivost|ranjivost]] [[Sistem za rezervne kopije|sistema za rezervne kopije]] u kojoj su kopije dostupne iz iste mreže ili sa istih naloga kao i originali, pa napad koji uništi ili šifruje originale može na isti način da uništi ili šifruje i kopije.

## Primer
Server za rezervne kopije firme [[Fakturis]] nalazi se u istom segmentu mreže kao poslovni računari, a kopije se čuvaju u deljenom folderu kome se pristupa Stefanovim administratorskim nalogom iz direktorijuma. Stefan se ranije prijavljivao na Jelenin laptop radi održavanja, pa su njegovi pristupni podaci ostali sačuvani na njemu. Kada ransomware grupa preuzme Jelenin laptop i dođe do tih podataka, šifruje i skladište dokumenata i sve kopije za poslednjih 30 dana. Kopije nisu ni šifrovane, pa ih napadač koji im pristupi može i pročitati.

## Napomene
- Kopija koja nije zaštićena ne može da posluži kao [[Korektivna kontrola|korektivna kontrola]] baš u napadu zbog kog najčešće postoji.
- Uz izolaciju, važno je i da se vraćanje podataka redovno proba. Za kopiju iz koje podaci nikad nisu vraćani ne zna se da li firma iz nje može da se oporavi.
