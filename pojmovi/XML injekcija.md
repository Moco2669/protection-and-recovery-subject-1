---
tip: pojam
aliases: [XML injection, XML tag injection, ubacivanje XML oznaka]
izvor: 'MITRE CWE-91: https://cwe.mitre.org/data/definitions/91.html; W3C, XML 1.0 (Fifth Edition): https://www.w3.org/TR/xml/; W3C, XML Schema Part 0: Primer (Second Edition): https://www.w3.org/TR/xmlschema-0/'
status: predlog
sloj: jezgro
---
# XML injekcija (XML injection)

## Definicija
XML injekcija je [[Injekcioni napad|injekcioni napad]] u kome napadač u vrednost koju komponenta ugrađuje u XML dokument ubacuje XML oznake ili posebne znakove, kako bi promenio strukturu dokumenta koji komponenta proizvodi.

## Primer
U ilustrativnoj razmeni e-faktura, [[Softverski proizvod|proizvod]] [[Fakturis|Fakturisa]] izdatu fakturu izvozi kao XML dokument. Element `<izdavalac>` upisuje sam, iz podataka naloga, a napomenu prepisuje iz forme spajanjem teksta. Faktura koju izdaje firma A, sa PIB-om 101111111, izgleda ovako:

```xml
<faktura>
  <broj>2026-117</broj>
  <napomena>Rok plaćanja 15 dana</napomena>
  <izdavalac>
    <pib>101111111</pib>
    <racun>160-0000000000001-11</racun>
  </izdavalac>
  <ukupno valuta="RSD">12000</ukupno>
</faktura>
```

Firma B, takođe korisnik Fakturisa, pri uvozu izdavaoca prepoznaje po PIB-u. Napadač je registrovan kao korisnik A i u napomenu fakture za firmu B upisuje:

```
x</napomena><izdavalac><pib>102222222</pib><racun>RACUN-NAPADACA</racun></izdavalac><napomena>x
```

Izvezeni dokument je i dalje dobro formiran, ali sada ima redosled `napomena`, `izdavalac`, `napomena`, `izdavalac`. Prvi `<izdavalac>` je napadačev, sa PIB-om stvarnog dobavljača firme B (102222222) i napadačevim računom. Ishod zavisi od uvoza u B:
- ako uvoz bira prvi element `izdavalac`, faktura se prikazuje kao da dolazi od poznatog dobavljača, i to je [[Lažno predstavljanje|lažno predstavljanje]] izdavaoca i [[Narušavanje integriteta podataka|narušavanje integriteta]] fakture;
- ako uvoz proverava dokument prema šemi koja dozvoljava jedan `izdavalac` u zadatom redosledu, dokument se odbija i napad ostaje neuspeo pokušaj.

Ranjiv je izvoz kod A, jer je napomenu ugradio kao strukturu. Scenario je ilustracija, a ne potvrđena ranjivost Fakturisa.

Kontraprimer: ako izvoz gradi dokument XML bibliotekom, ista napomena postaje tekst `x&lt;/napomena&gt;&lt;izdavalac&gt;…`, a uvoz u B vidi samo neobičnu napomenu. Nije XML injekcija ni kada napadač sam pošalje ceo XML dokument sa deklaracijom spoljnog entiteta. To je [[Napad spoljnim XML entitetom]].

## Napomene
- **Ko kontroliše šta.** Napadač kontroliše samo vrednost jednog polja. Komponenta koja sastavlja dokument kontroliše ostatak. Napad uspeva kada ta vrednost postane struktura. Zato se XML injekcija sprečava tamo gde se dokument piše, a ne tamo gde se čita. Isti scenario, od strane ranjivosti, opisan je u belešci [[Injekciona ranjivost]].
- **Dobro formiran, validan i ispravan prema šemi.** Dokument je dobro formiran kada poštuje sintaksna pravila XML-a, na primer kada je svaki element zatvoren i postoji tačno jedan koreni element. [[Parser]] odbija dokument koji nije dobro formiran, pa napadač zatvara element koji je otvorio programer (`</napomena>`) i otvara novi na kraju (`<napomena>`). Dobro formiran dokument nije time i validan. Validnost prema DTD-u, opisanom u belešci [[XML entitet]], i ispravnost prema XSD šemi zasebne su provere, i parser ih radi samo kada je tako podešen.
- **Šta provera prema XSD šemi može, a šta ne.** XSD je W3C jezik za opis dozvoljene strukture i sadržaja dokumenta. U XSD-u je podrazumevana vrednost i za `minOccurs` i za `maxOccurs` jednaka 1, pa se element bez drugačijeg navoda javlja tačno jednom. Elementi u sekvenci moraju da dođu zadatim redom. Šema koja to propisuje odbila bi dokument iz primera. Provera ne otkriva ubačenu strukturu koja poštuje šemu, na primer dodatni element na mestu gde ga šema dozvoljava više puta. Ne utvrđuje ni da li je dozvoljen oblik nastao kako je programer nameravao.
- **Posledica zavisi od primaoca.** Kada dokument sadrži dva elementa istog imena, različiti programi ih različito obrađuju. XPath funkcija `string()` vraća vrednost prvog čvora po redosledu u dokumentu. Biblioteka koja dokument preslikava u objekte može da zadrži poslednju vrednost ili da prijavi grešku. Zato se ishod XML injekcije procenjuje za konkretnog primaoca.
- **Posebni znakovi.** U tekstualnom sadržaju elementa znakovi `<` i `&` ne smeju se pojaviti doslovno i zapisuju se kao `&lt;` i `&amp;`. Ne sme se pojaviti ni niz `]]>`, pa se `>` u njemu zapisuje kao `&gt;`. U vrednosti atributa takođe su zabranjeni `<` i `&`, kao i navodnik kojim je vrednost omeđena, koji se zapisuje kao `&quot;` ili `&apos;`. Na tim pravilima zasniva se [[Neutralizacija specijalnih elemenata|neutralizacija specijalnih elemenata]] za XML. XML biblioteke koje grade dokument primenjuju ih same.
- **Razlika od XPath injekcije.** XML injekcija menja dokument. [[XPath injekcija]] ostavlja dokument netaknutim i menja izraz kojim se iz njega biraju podaci.
- **Razlika od napada spoljnim XML entitetom.** Kod XML injekcije ranjivost je u komponenti koja piše XML, a napadač kontroliše samo vrednost. Kod [[Napad spoljnim XML entitetom|napada spoljnim XML entitetom]] napadač dostavlja ceo dokument, a ranjivost je u podešavanju parsera koji ga čita. U ovoj bazi taj napad se obrađuje zasebno zbog drugačijeg mehanizma, što je objašnjeno u njegovoj belešci.
- **Terminologija u izvorima.** CWE-91 je klasa „XML Injection“ ispod CWE-74. U istom unosu MITRE kao alternativni naziv navodi „Blind XPath Injection“, a CWE-643 (XPath injekcija) vodi kao podvrstu CWE-91, u širem smislu jezika vezanih za XML. Ova baza XML injekciju i XPath injekciju razdvaja, jer je jezik koji tumači ubačeni deo različit. CAPEC-250 pod istim nazivom opisuje uglavnom napade na XML baze, sličnije XPath injekciji.
- **Zaštita.** Dokument se gradi bibliotekom koja vrednosti sama zapisuje kao tekst, ili se vrednost neutralizuje pravilima XML-a. Videti [[Neutralizacija specijalnih elemenata]]. [[Validacija ulaza]] pomaže samo kada polje po prirodi ne sme da sadrži te znakove. Napomena sme da sadrži „Cena < 1000“, pa validacija ovde nije dovoljna. Provera prema šemi kod primaoca je dopunska mera, a ne zamena za ispravan izvoz.
- XML je u bazi pretpostavljen pojam. Fakturis u osnovnoj studiji ne koristi XML. Razmena e-faktura je ilustrativna funkcija opisana u belešci konteksta, a elementi u primeru su pojednostavljeni i ne prate nijedan konkretan standard e-faktura.
