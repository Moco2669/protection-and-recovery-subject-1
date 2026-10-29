---
tip: pojam
aliases: [component type, tip komponente]
izvor: ZOSS 03 (predavanje); srodno: NIST SP 800-53 Rev. 5, Appendix A Glossary, "system component"
status: predlog
sloj: temelj
---
# Tip komponente sistema (component type)

## Definicija
Tip komponente sistema je grupa [[Komponenta sistema|komponenti sistema]] iste prirode, određene time da li je komponenta program, uređaj, sredstvo za prenos podataka između drugih komponenti, osoba ili prostor.

## Primer
Komponente firme [[Fakturis]] po tipu:

| Tip | Komponente |
|---|---|
| softverska | [[Web aplikacija]], [[Baza podataka]], [[Repozitorijum izvornog koda]], [[Sistem za upravljanje nalozima]], [[Sistem za zapise o radu]] |
| hardverska | [[Server]] (aplikacioni server, GitLab server), [[Skladište dokumenata]] (NAS), [[Sistem za rezervne kopije]], [[Poslovni računar]] |
| mrežna | [[Mrežni prolaz]], [[Interna mreža]] |
| ljudska | [[Zaposleni]]: Jelena, Stefan, programeri, direktor i knjigovođa |
| fizička | server soba, kancelarija, napajanje |

## Napomene
- Isti uređaj se posmatra na više nivoa: laptop je hardverska komponenta, a Windows na njemu softverska. Ruter je uređaj, ali ga svrstavamo u mrežne komponente po ulozi.
- Tipovi su korisni jer se slabosti i kontrole često vezuju za ceo tip. Socijalni inženjering cilja ljudske komponente, fabričke lozinke su česte kod mrežnih, a zaključavanje prostorija štiti fizičke.
- Beleška konteksta [[Fakturis]] koristi i drugu podelu, po ulozi u poslovanju: ljudi i radno okruženje, mreža, aplikacija i serversko okruženje, čuvanje podataka, razvoj i održavanje, zajedničke funkcije zaštite. Dve podele se ne isključuju.
