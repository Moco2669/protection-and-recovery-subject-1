---
tip: pojam
aliases: [parameterization]
izvor: 'OWASP Injection Prevention Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Injection_Prevention_Cheat_Sheet.html; MITRE CWE-116: https://cwe.mitre.org/data/definitions/116.html; Java SE 21, XPathVariableResolver: https://docs.oracle.com/en/java/javase/21/docs/api/java.xml/javax/xml/xpath/XPathVariableResolver.html'
status: predlog
sloj: jezgro
---
# Parametrizacija (parameterization)

## Definicija
Parametrizacija je [[Tehnička kontrola|tehnička]] i [[Preventivna kontrola|preventivna kontrola]] u kojoj komponenta [[Parser|parseru]] ili [[Interpreter|interpreteru]] predaje strukturu izraza, upita, komande ili šablona odvojeno od vrednosti, preko interfejsa koji vrednosti prenosi kao podatke i nikada ih ne tumači kao sintaksu tog jezika.

## Primer
U ilustrativnoj pretrazi zbirnog XML dokumenta iz beleške [[XPath injekcija]], [[Softverski proizvod|proizvod]] [[Fakturis|Fakturisa]] više ne sastavlja izraz spajanjem teksta. Izraz je stalan, a vrednosti se predaju kroz kontekst izračunavanja, u Javi preko interfejsa `XPathVariableResolver`:

```java
XPath xp = XPathFactory.newInstance().newXPath();
xp.setXPathVariableResolver(ime -> switch (ime.getLocalPart()) {
    case "korisnik" -> idKorisnika;
    case "naziv" -> naziv;
    default -> null;
});
NodeList fakture = (NodeList) xp.evaluate(
    "//faktura[korisnik=$korisnik and kupac/naziv=$naziv]", dokument, XPathConstants.NODESET);
```

Biblioteka parsira tekst izraza, koji je isti za svaki zahtev. Kada pri izračunavanju dođe do reference `$naziv`, traži njenu vrednost od resolvera i koristi je kao tekstualnu vrednost. Ako korisnik u naziv upiše `x' or '1'='1`, apostrofi ostaju deo vrednosti, a izraz traži kupca sa baš tim nazivom i ne pronalazi ga. Napad iz beleške [[XPath injekcija]] ne uspeva, jer ulaz više ne učestvuje u parsiranju izraza.

Kontraprimer: ako proizvod izraz i dalje sastavlja spajanjem teksta, a pre toga iz naziva ukloni apostrofe, to nije parametrizacija. Struktura i vrednost su i dalje u istom tekstu, a bezbednost zavisi od toga da li je uklanjanje potpuno. Usput se menja i ispravan naziv „O'Brien d.o.o.“.

## Napomene
- **Šta radi, a šta ne.** Parametrizacija obezbeđuje da tekst strukture ne zavisi od ulaza, pa vrednost ne može da promeni strukturu. Ne proverava da li vrednost ima smisla, što radi [[Validacija ulaza|validacija ulaza]]. Ne menja znakove vrednosti, što radi [[Neutralizacija specijalnih elemenata|neutralizacija specijalnih elemenata]]. Najpoznatiji oblik su parametrizovani SQL upiti, ali pojam je širi: MITRE istu meru opisuje kao strukturisane mehanizme koji automatski razdvajaju podatke od koda, a za XPath navodi parametrizovane upite.
- **Mesto u preporukama.** OWASP kao željeno rešenje navodi bezbedan interfejs koji potpuno izbegava interpreter ili pruža parametrizovan interfejs. Ako se funkcija može ostvariti bez interpretera, na primer bibliotekom za ZIP arhive umesto komande, to je još bolje od parametrizacije.
- **Primena na napade iz ove grane:**
  - **XPath.** Promenljive `$ime` i `XPathVariableResolver`, kao u primeru. Pojam promenljive objašnjen je u belešci [[XPath]].
  - **NoSQL (MongoDB).** Upit koji se gradi kao objekat u kodu sam po sebi nije parametrizovan. Na mestu vrednosti drajver prihvata i objekat, pa objekat `{"$ne": ""}` iz zahteva postaje operator, kao u primeru beleške [[NoSQL injekcija]]. Najbliži oblik parametrizacije je izričit oblik `{ kod: { $eq: vrednost } }`, koji MongoDB preporučuje za vrednosti od korisnika. Taj oblik mesto u upitu određuje kao poređenje sa vrednošću, a dokumentacija za njega opisuje poređenje sa vrednošću dokumenta. Objekat sa `$ne` zato postaje vrednost sa kojom se kod poredi, pa upit ne pronalazi fakturu. `$eq` ne proverava tip: zahtev sa objektom i dalje stiže do baze. Proizvod zato uz `$eq` proverava i da je kod tekst ([[Validacija ulaza]]).
  - **OS komande.** Program se pokreće bez shell-a, a program i argumenti predaju se kao lista, u Python-u `subprocess.run(["zip", putanja_arhive, *datoteke])`. Operativni sistem pokreće program neposredno i predaje mu argumente kao zasebne nizove znakova, pa nijedan shell ne parsira tekst i znakovi `;`, `#` i `*` nemaju posebno značenje (primer u belešci [[Injekcija OS komandi]]). To ne rešava ubacivanje argumenata: pozvani program sam tumači svoje argumente i vrednost koja počinje crticom može da pročita kao opciju. OWASP zato navodi da razdvajanje argumenata ne zamenjuje njihovu proveru i da se, za komande koje to podržavaju, kraj opcija označava sa `--`. U primeru Fakturisa naziv je deo putanje `/tmp/arhive/…`, pa argument ne može da počne crticom.
  - **Šabloni.** Proizvod koristi fiksni šablon, a korisnikov tekst predaje kao vrednost u kontekstu, na primer `render(poruka=tekst_korisnika)`. OWASP ovu meru izričito poredi sa parametrizovanim upitom. Ona važi samo kada korisnik uređuje podatak. Kada korisnik namerno uređuje sam šablon, nema odvojene vrednosti koju bi trebalo predati, pa se primenjuju mere iz beleške [[Serverska injekcija šablona]].
  - **XML dokument.** Kada izvoz gradi dokument XML bibliotekom, struktura nastaje pozivima koji prave elemente, a napomena se predaje kao tekstualni čvor. U tom koraku vrednost ne može da postane element, što liči na parametrizaciju. Dokument se ipak na kraju zapisuje kao tekst, i tada biblioteka mora da primeni pravila XML-a za tekst i atribute. To je neutralizacija koju radi biblioteka, a ne zaseban kanal za vrednosti kakav postoji kod XPath promenljivih. Bezbednost izvoza iz beleške [[XML injekcija]] zato zavisi od ispravne neutralizacije u biblioteci (videti [[Neutralizacija specijalnih elemenata]]).
  - **Napad spoljnim XML entitetom.** Parametrizacija ne pomaže, jer napadač dostavlja ceo dokument i ne ubacuje vrednost u strukturu koju piše proizvod. Zaštita je podešavanje parsera, opisano u belešci [[Napad spoljnim XML entitetom]].
- **Ograničenja.** Ne mogu se parametrizovati delovi strukture koji se namerno menjaju, kao ime polja po kome se sortira ili naziv programa koji se pokreće. Za njih se koristi lista dozvoljenih vrednosti. Parametrizacija ne pomaže ni kada program vrednost kasnije, u drugom koraku, ponovo ugradi u tekst bez parametrizacije, kao kod injekcije drugog reda opisane u belešci [[Injekcioni napad]]. OWASP upozorava i na interfejse koji su spolja parametrizovani, ali vrednost iznutra ponovo ugrađuju u tekst.
- Pretraga zbirnog dokumenta, pregled fakture, arhiva i podsetnik su ilustrativne funkcije Fakturisa, opisane u belešci konteksta. Izbor Jave, Python-a i MongoDB-a je ilustrativan.
