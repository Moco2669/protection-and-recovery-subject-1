---
tip: pojam
aliases: [system component, komponenta]
izvor: NIST SP 800-53 Rev. 5, Appendix A Glossary, "system component" (SP 800-128)
status: predavanje
sloj: temelj
---
# Komponenta sistema (system component)

## Definicija
Komponenta sistema je deo sistema organizacije u kom se [[Resurs|resurs]] skladišti, obrađuje, ili kroz koji se prenosi. Može biti softverska, hardverska ili mrežna, ali i ljudska ili fizička, kao zaposleni koji obrađuje podatke ili arhiva papirne dokumentacije.

## Primer
Put jedne fakture u firmi [[Fakturis]]: korisnik je unosi u web aplikaciju preko mrežnog prolaza, aplikacija je upisuje u bazu podataka, generiše PDF i čuva ga u skladištu dokumenata, a noću se faktura kopira na server za rezervne kopije. Kada korisnik zatraži ispravku, fakturu obrađuje i Jelena iz podrške. Mrežni prolaz, web aplikacija, baza, skladište dokumenata, server za rezervne kopije i Jelena su komponente sistema, jer faktura kroz njih prolazi ili se u njima nalazi.

Kontraprimer: laptop kupca koji otvara link ka fakturi takođe sadrži fakturu, ali nije komponenta sistema, jer je izvan [[Granica sistema|granice sistema]] firme.

## Napomene
- Podela na komponente je logička. Aplikacija, operativni sistem servera i baza su različite komponente i kada rade na istoj mašini, jer imaju različite uloge, ranjivosti i kontrole.
- Komponente se grupišu po prirodi u [[Tip komponente sistema|tipove komponenti]].
- Konkretne komponente opisane u bazi, po celinama iz konteksta [[Fakturis]]:
  - ljudi i radno okruženje: [[Zaposleni]], [[Poslovni računar]]
  - mreža i komunikacija: [[Mrežni prolaz]], [[Interna mreža]]
  - aplikacija i serversko okruženje: [[Server]], [[Web aplikacija]]
  - čuvanje podataka: [[Baza podataka]], [[Skladište dokumenata]]
  - razvoj i održavanje: [[Repozitorijum izvornog koda]]
  - zajedničke funkcije zaštite i podrške: [[Sistem za upravljanje nalozima]], [[Sistem za zapise o radu]], [[Sistem za rezervne kopije]]
