---
tip: pojam
aliases: [parser, sintaksni analizator, parsiranje, parsing]
izvor: 'Nystrom, Crafting Interpreters, 2021, poglavlje 2: https://craftinginterpreters.com/a-map-of-the-territory.html; W3C, XML 1.0 (Fifth Edition): https://www.w3.org/TR/xml/'
status: predlog
sloj: temelj
---
# Parser (parser)

## Definicija
Parser je deo programa koji ulaz zapisan na nekom jeziku ili u nekom formatu, kao tekst ili kao niz bajtova, proverava prema pravilima njegove sintakse i pretvara u strukturu s kojom program dalje radi, najčešće u stablo.

## Primer
Kada bi korisnik [[Fakturis|Fakturisa]] uvezao XML e-fakturu, [[Softverski proizvod|softverski proizvod]] bi tekst datoteke predao XML parseru. Parser bi proverio da li su elementi ispravno otvoreni i zatvoreni i napravio stablo u kome je `<faktura>` koren, a `<broj>`, `<napomena>` i `<izdavalac>` njegovi potomci. Proizvod zatim čita vrednosti iz stabla, a ne iz sirovog teksta.

Kontraprimer: kada proizvod istu datoteku samo sačuva u [[Skladište datoteka|skladištu datoteka]], ne parsira je. Datoteka se tretira kao niz bajtova čiji sadržaj niko ne tumači.

## Napomene
- Parser određuje šta je u ulazu struktura, a šta vrednost. U `<napomena>Rok 15 dana</napomena>` oznake su struktura, a „Rok 15 dana“ vrednost. [[Injekciona ranjivost]] nastaje kada deo [[Nepouzdan ulaz|nepouzdanog ulaza]] parser pročita kao strukturu.
- Rezultat ne mora biti stablo. Parser može da vrati niz događaja (na primer „počinje element `napomena`“, „tekst“, „završava se element“) ili da popuni objekte programa. Bitno je da posle parsiranja program radi sa strukturom, a ne sa sirovim ulazom.
- **Parsiranje nije izvršavanje komandi.** Parser ne izvršava naredbe zapisane u ulazu. To radi [[Interpreter|interpreter]]. Ipak, parser tokom obrade može da obavi radnje koje propisuje sam format. XML parser referencu na [[XML entitet|XML entitet]] zamenjuje sadržajem entiteta, a taj sadržaj može da učita iz datoteke ili sa mreže. Zato i sam parser može biti ranjiv, kao u [[Napad spoljnim XML entitetom|napadu spoljnim XML entitetom]], iako ne izvršava ničije komande.
- Parseri su prisutni i tamo gde se ne vide. [[Serverski program|Serverski program]] parsira [[HTTP]] zahtev iz [[Tok bajtova|toka bajtova]], a biblioteke parsiraju JSON telo zahteva, XML i datoteke formata koji u sebi sadrže XML.
- Kod programskih jezika parsiranju obično prethodi podela teksta na osnovne jedinice (tokene), a parser od niza tokena gradi stablo. Kod XML-a obe faze najčešće obavlja ista biblioteka.
- Specifikacija XML-a program koji čita XML dokumente i daje pristup njihovom sadržaju i strukturi naziva XML procesor. To je XML parser u smislu ove beleške. Naziv se ne koristi za parsere drugih formata.
- U srpskoj literaturi o prevodiocima koristi se i „sintaksni analizator“. U praksi je ustaljeniji „parser“, pa je on glavni termin.
