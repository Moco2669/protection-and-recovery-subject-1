---
tip: pojam
aliases: [XPath injection]
izvor: 'MITRE CWE-643: https://cwe.mitre.org/data/definitions/643.html; OWASP, XPATH Injection: https://owasp.org/www-community/attacks/XPATH_Injection; OWASP, Blind XPath Injection: https://owasp.org/www-community/attacks/Blind_XPath_Injection'
status: predlog
sloj: jezgro
---
# XPath injekcija (XPath injection)

## Definicija
XPath injekcija je [[Injekcioni napad|injekcioni napad]] u kome napadač u vrednost koju komponenta ugrađuje u [[XPath]] izraz ubacuje sintaksu XPath-a, kako bi izraz iz XML dokumenta izabrao druge čvorove od onih koje je programer predvideo.

## Primer
U ilustrativnoj funkciji pretrage, [[Softverski proizvod|proizvod]] [[Fakturis|Fakturisa]] sve izvezene e-fakture, za sve korisnike, drži u jednom zbirnom XML dokumentu u [[Skladište datoteka|skladištu datoteka]]. Struktura dokumenta prikazana je u belešci [[XPath]]. Fakture prijavljenog korisnika proizvod bira izrazom koji sastavlja spajanjem teksta:

```
"//faktura[korisnik='" + idKorisnika + "' and kupac/naziv='" + naziv + "']"
```

Korisnik 17 u polje za naziv kupca upisuje `x' or '1'='1`. Izraz postaje:

```
//faktura[korisnik='17' and kupac/naziv='x' or '1'='1']
```

Prvi apostrof iz unosa zatvara literal koji je otvorio programer, a poslednji apostrof izraza zatvara literal `'1`, pa je izraz sintaksno ispravan. U XPath-u `and` ima viši prioritet od `or`, pa se uslov čita kao `(korisnik='17' and kupac/naziv='x') or '1'='1'`. Drugi deo je uvek tačan, pa uslov važi za svaki element `faktura` i izraz bira fakture svih korisnika. Ishod je [[Narušavanje poverljivosti podataka|narušavanje poverljivosti]]. Scenario je ilustracija, a ne potvrđena ranjivost Fakturisa.

Kontraprimer: kada korisnik u isto polje upiše `O'Brien d.o.o.`, a proizvod naziv predaje kao vrednost promenljive `$naziv`, izraz ostaje `//faktura[korisnik=$korisnik and kupac/naziv=$naziv]`. Apostrof je deo vrednosti, i izraz samo ne pronađe takvog kupca.

## Napomene
- **Dokument je netaknut.** Za razliku od [[XML injekcija|XML injekcije]], napadač ne menja nijedan element dokumenta. Menja uslov kojim se iz dokumenta bira.
- **Autorizacija i obim posledice.** Pošto XPath ne sprovodi autorizaciju po elementima (videti [[XPath]]), OWASP navodi da napadač može da dobije ceo dokument nad kojim se izraz izračunava. U primeru je uslov `korisnik='17'` jedina granica između podataka različitih korisnika, jer su svi u istom dokumentu. Kada bi proizvod izraz izračunavao samo nad dokumentom prijavljenog korisnika, ista injekcija bi otkrila samo njegove fakture. To je ograničenje koje sprovodi aplikacija, a ne XPath.
- **Slepa XPath injekcija.** Kada odgovor ne prikazuje izabrane čvorove, nego samo da li je nešto pronađeno, napadač postavlja niz pitanja na koja je odgovor tačno ili netačno. OWASP opisuje ispitivanje strukture dokumenta funkcijom `count()` i čitanje vrednosti znak po znak funkcijama `string-length()` i `substring()`. MITRE CWE-91 navodi „Blind XPath Injection“ kao alternativni naziv.
- **Mesto u klasifikaciji.** CWE-643 je podvrsta i CWE-943 (upiti nad podacima) i CWE-91 (XML injekcija). Opis u CWE-643 pominje XML bazu. Isti mehanizam važi i kada izraz izračunava biblioteka nad datotekom, kao u primeru.
- **Zaštita.** Glavna zaštita je [[Parametrizacija|parametrizacija]]: vrednosti se predaju kao XPath promenljive, na primer preko Java interfejsa `XPathVariableResolver`. Ručna [[Neutralizacija specijalnih elemenata|neutralizacija]] je u XPath 1.0 nezgodna zbog pravila o navodnicima u literalima, opisanih u belešci [[XPath]]. [[Validacija ulaza]] pomaže za polja strogog oblika, kao identifikator korisnika. Uzimanje identifikatora iz sesije, a ne iz zahteva, ne sprečava napad iz primera, jer je ubačen u drugo polje.
- Zbirni dokument za sve korisnike je namerno loš izbor dizajna, uveden da bi se videla posledica. To nije opis stvarne arhitekture Fakturisa.
