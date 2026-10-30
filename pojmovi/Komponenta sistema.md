---
tip: pojam
aliases: [system component, komponenta]
izvor: ZOSS 03, slajd Komponenta sistema (system component)
status: predavanje
sloj: temelj
---
# Komponenta sistema (system component)

## Definicija
Komponenta sistema je deo sistema organizacije u kom se [[Resurs|resurs]] skladišti, obrađuje, ili kroz koji se prenosi. Može biti softverska, hardverska ili mrežna, ali i ljudska ili fizička, kao zaposleni koji obrađuje podatke ili arhiva papirne dokumentacije.

## Primer
Put jedne fakture u firmi [[Fakturis]]: korisnik je unosi preko mrežnog prolaza u web aplikaciju, aplikacija je upisuje u bazu podataka i čuva PDF u skladištu dokumenata. Kada zatraži ispravku, fakturu obrađuje i Jelena iz podrške. Mrežni prolaz, web aplikacija, baza, skladište i Jelena su komponente sistema, jer se faktura u njima nalazi ili kroz njih prenosi.

Izmene koda idu sa poslovnog računara programera u repozitorijum, a odatle na aplikacioni server. To su takođe komponente, jer se izvorni kod u njima čuva ili kroz njih prenosi.

Kontraprimer: PayNet obrađuje plaćanje, ali je servis druge firme, van sistema Fakturisa. Komponenta je samo deo web aplikacije koji PayNet-u šalje zahtev i prima obaveštenje. Kartica kupca u sistem ne ulazi. Laptop kupca koji otvara link ka fakturi takođe nije komponenta ovog sistema.

## Napomene
- Podela je logička. Aplikacija, operativni sistem servera i baza ostaju različite komponente i kada rade na istoj mašini, jer imaju različite uloge.
- Konkretne komponente u ovoj bazi: [[Zaposleni]], [[Poslovni računar]], [[Mrežni prolaz]], [[Interna mreža]], [[Server]], [[Web aplikacija]], [[Baza podataka]], [[Skladište dokumenata]], [[Repozitorijum izvornog koda]], [[Sistem za rezervne kopije]].
