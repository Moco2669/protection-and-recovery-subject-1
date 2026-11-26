---
tip: pojam
aliases: [XPath, XML Path Language, XPath izraz]
izvor: 'W3C, XPath 1.0: https://www.w3.org/TR/xpath-10/; W3C, XPath 3.1: https://www.w3.org/TR/xpath-31/'
status: predlog
sloj: temelj
---
# XPath (XML Path Language)

## Definicija
XPath je jezik izraza kojim se iz XML dokumenta biraju čvorovi i vrednosti prema njihovom položaju u stablu dokumenta i prema uslovima nad njihovim sadržajem.

## Primer
U ilustrativnoj funkciji pretrage, [[Softverski proizvod|proizvod]] [[Fakturis|Fakturisa]] izvezene e-fakture drži u jednom zbirnom XML dokumentu. Svaka faktura u njemu, pored podataka iz e-fakture prikazane u belešci [[XML injekcija]], ima i oznaku korisnika Fakturisa koji ju je izdao i podatke o kupcu:

```xml
<fakture>
  <faktura>
    <korisnik>17</korisnik>
    <kupac><naziv>Mesara Zlatibor</naziv></kupac>
    <ukupno valuta="RSD">12000</ukupno>
  </faktura>
  <!-- ostale fakture svih korisnika -->
</fakture>
```

Izraz

```
//faktura[korisnik='17' and kupac/naziv='Mesara Zlatibor']/ukupno
```

bira element `ukupno` svake fakture korisnika 17 izdate kupcu sa tim nazivom. `//faktura` pronalazi elemente `faktura` bilo gde u stablu, uslov u uglastim zagradama zadržava samo one koji ga ispunjavaju, a `/ukupno` prelazi na njihov potomak. Izraz izračunava biblioteka u proizvodu, nad dokumentom koji je [[Parser|parser]] prethodno pretvorio u stablo.

## Napomene
- **Ko izvršava izraz.** XPath najčešće izračunava biblioteka u samom programu, kao [[Interpreter|interpreter]] nad dokumentom u memoriji, a ne poseban server baze. Beleška [[Upitni jezik]] vezuje upitni jezik za [[Skladište podataka|skladište podataka]], pa je XPath ovde definisan nezavisno. Namena mu je ista, da opiše koje podatke treba pronaći, a MITRE CWE-943 ga svrstava među jezike upita.
- **XPath ne sprovodi autorizaciju.** XPath nema naloge ni prava po elementima. Izraz može da izabere bilo koji deo dokumenta nad kojim se izračunava. Aplikacija može da ograniči šta je dostupno izborom dokumenta ili podstabla nad kojim izraz izvršava, na primer tako da svaki korisnik ima zaseban dokument. Ako su podaci više korisnika u istom dokumentu, jedina granica je uslov koji je programer napisao u izrazu. Na tome se zasniva [[XPath injekcija]].
- **Promenljive.** Izraz može da sadrži reference na promenljive oblika `$ime`. Njihove vrednosti ne zapisuju se u tekstu izraza, nego ih program predaje kroz kontekst izračunavanja. U Javi to radi interfejs `XPathVariableResolver`. To omogućava [[Parametrizacija|parametrizaciju]] XPath izraza.
- **Literali i navodnici.** Tekstualna vrednost u izrazu piše se između jednostrukih ili dvostrukih navodnika. Gramatika XPath 1.0 ne predviđa način da se unutar literala zapiše isti navodnik kojim je literal otvoren, pa se vrednost sa oba navodnika sastavlja funkcijom `concat()`. Zbog toga je ručna [[Neutralizacija specijalnih elemenata|neutralizacija]] u XPath 1.0 nezgodna.
- **Operatori.** U XPath-u `or` ima najniži prioritet, a `and` viši, pa se `a and b or c` čita kao `(a and b) or c`. To je bitno za razumevanje [[XPath injekcija|XPath injekcije]].
- **Verzije.** Postoje preporuke XPath 1.0 (1999) i XPath 3.1 (2017). Novije verzije dodaju tipove, funkcije i strukture podataka. Primeri u ovoj bazi koriste sintaksu XPath 1.0. Isti jezik izraza koristi se i u XSLT-u i XQuery-ju.
- Zbirni dokument i njegovi elementi su ilustrativni. Elementi `korisnik` i `kupac` dodati su samo za potrebe pretrage i ne pripadaju pojednostavljenoj e-fakturi iz beleške [[XML injekcija]].
