---
tip: pojam
aliases: [unpatched software, vulnerable and outdated components, zastarela komponenta]
izvor: OWASP Top 10:2021, A06:2021 Vulnerable and Outdated Components (u izdanju 2025 deo kategorije A03:2025 Software Supply Chain Failures); CWE-1395 Dependency on Vulnerable Third-Party Component
status: predlog
sloj: jezgro
---
# Nezakrpljen softver (unpatched software)

## Definicija
Nezakrpljen softver je [[Ranjivost|ranjivost]] [[Komponenta sistema|komponente sistema]], najčešće [[Server|servera]] ili [[Poslovni računar|poslovnog računara]], koja izvršava verziju softvera sa javno poznatom [[Slabost|slabošću]] za koju je proizvođač već objavio ispravku (zakrpu), a koju je na toj komponenti moguće iskoristiti.

## Primer
Na aplikacionom serveru firme [[Fakturis]] Ubuntu i nginx nisu ažurirani od marta. Za verziju nginx-a koja radi na serveru u međuvremenu je objavljena slabost koja se može iskoristiti posebno oblikovanim HTTP zahtevom, a server je dostupan sa interneta.

Isti problem postoji u samoj [[Web aplikacija|web aplikaciji]]. PDF fakture generiše biblioteka PdfGen 2.3, za koju je javno objavljeno da, kada HTML šablon sadrži sliku sa adresom oblika `file:///...`, u PDF ubacuje sadržaj fajla sa servera. Verzija 2.4 to ispravlja. Dok korisnici nisu mogli da utiču na slike u šablonu, to je bila samo slabost. Kada je dodata opcija „logo firme preko adrese slike“, korisnik može da upiše `file:///etc/passwd` i dobije sadržaj tog fajla u svojoj fakturi.

Na poslovnim računarima Windows nema uključeno automatsko ažuriranje.

## Napomene
- Javno poznate slabosti konkretnih proizvoda vode se u katalogu CVE, gde se nazivaju ranjivostima (vulnerabilities). U ovoj bazi to su slabosti proizvoda, a ranjivost postaju tek kada su iskoristive na našoj komponenti.
- Rizik raste kada se zakrpa objavi, jer tada i napadači saznaju šta je ispravljeno.
