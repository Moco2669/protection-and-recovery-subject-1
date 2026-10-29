---
tip: pojam
aliases: [unpatched software, vulnerable and outdated components, zastarela komponenta]
izvor: OWASP Top 10:2021, A06:2021 Vulnerable and Outdated Components (u izdanju 2025 deo kategorije A03:2025 Software Supply Chain Failures); CWE-1395 Dependency on Vulnerable Third-Party Component
status: predlog
sloj: jezgro
---
# Nezakrpljen softver (unpatched software)

## Definicija
Nezakrpljen softver je [[Slabost|slabost]] [[Komponenta sistema|komponente sistema]] koja izvršava verziju softvera sa javno poznatom slabošću za koju je proizvođač već objavio ispravku (zakrpu).

## Primer
Aplikacija [[Fakturis]] generiše PDF fakture bibliotekom PdfGen 2.3. Za tu verziju je javno objavljeno da, kada HTML šablon sadrži sliku sa adresom oblika `file:///...`, biblioteka u PDF ubacuje sadržaj fajla sa servera. Verzija 2.4 to ispravlja. Dok aplikacija nije dozvoljavala korisnicima da utiču na slike u šablonu, to je bila samo slabost. Kada je dodata opcija „logo firme preko adrese slike“, korisnik može da upiše adresu `file:///etc/passwd` i dobije sadržaj tog fajla u svojoj fakturi.

Isti problem imaju aplikacioni server, na kom Ubuntu i nginx nisu ažurirani od marta, i poslovni računari, na kojima Windows nema uključeno automatsko ažuriranje.

## Napomene
- Javno poznate slabosti konkretnih proizvoda vode se u katalogu CVE, gde se nazivaju ranjivostima (vulnerabilities). U ovoj bazi to su slabosti proizvoda, a ranjivost postaju tek kada su iskoristive na našoj komponenti.
- Rizik raste kada se zakrpa objavi, jer tada i napadači saznaju šta je ispravljeno.
