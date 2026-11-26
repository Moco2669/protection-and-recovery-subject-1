---
tip: pojam
aliases: [NoSQL injection, NoSQLi]
izvor: 'MITRE CWE-943: https://cwe.mitre.org/data/definitions/943.html; MongoDB Manual, How does MongoDB address SQL or Query injection?: https://www.mongodb.com/docs/manual/faq/fundamentals/; qs, README: https://github.com/ljharb/qs; Apache Cassandra, CQL: https://cassandra.apache.org/doc/latest/cassandra/developing/cql/index.html'
status: predlog
sloj: jezgro
---
# NoSQL injekcija (NoSQL injection)

## Definicija
NoSQL injekcija je [[Injekcioni napad|injekcioni napad]] u kome napadač, umesto vrednosti koju komponenta ugrađuje u upit NoSQL [[Baza podataka|baze podataka]], podmeće operator upitnog jezika te baze ili u vrednost ubacuje izraz koji baza izvršava, kako bi upit pronašao, izmenio ili izračunao nešto drugo od onoga što je programer predvideo.

## Primer
U ilustrativnoj funkciji pregleda fakture, kupac dobija broj fakture i kontrolni kod i bez naloga otvara fakturu. U ovoj varijanti fakture su u MongoDB-u, kao u primeru beleške [[Dokument-orijentisana baza podataka]]. [[Softverski proizvod|Proizvod]] [[Fakturis|Fakturisa]] prima JSON telo zahteva i vrednosti, bez provere tipa, stavlja u upit preko MongoDB drajvera za Node.js. Ovde je `db` već otvorena baza, a kod se izvršava u asinhronoj funkciji:

```js
const faktura = await db.collection("fakture").findOne({
  broj: telo.broj,
  kod: telo.kod
});
```

Ispravan zahtev je `{"broj": "2026-117", "kod": "7f3a9c21"}`. Napadač koji zna samo broj fakture šalje:

```json
{"broj": "2026-117", "kod": {"$ne": ""}}
```

Za `kod` proizvod sada ne predaje tekst, nego objekat sa operatorom `$ne` („nije jednako“). Uslov važi za svaki dokument čiji kod nije prazan tekst, a prema MongoDB dokumentaciji i za dokumente koji polje uopšte nemaju. `findOne` vraća fakturu iako napadač ne zna kod. Ishod je [[Narušavanje poverljivosti podataka|narušavanje poverljivosti]]. Ako napadač ni broj ne zna, može da pošalje `{"broj": {"$gt": ""}, "kod": {"$ne": ""}}`. Pošto MongoDB poredi samo vrednosti istog tipa, uslov `$gt: ""` važi za svaki neprazan tekstualni broj. Upit tada ispunjava više faktura, a `findOne` vraća jednu od njih, odnosno fakturu nekog kupca. Scenario je ilustracija, a osnovna studija koristi PostgreSQL.

Kontraprimer: ako napadač isti niz znakova pošalje kao tekst, `{"broj": "2026-117", "kod": "{\"$ne\": \"\"}"}`, baza traži fakturu čiji je kod doslovno taj tekst i ne pronalazi je. MongoDB dokumentacija objašnjava da klijent upit sastavlja kao BSON objekat, a ne kao tekst, pa vrednost tekstualnog tipa ostaje vrednost bez obzira na znakove koje sadrži. Napad zato zavisi od toga da li napadač može da promeni tip vrednosti ili da ubaci tekst u izraz koji baza izvršava.

## Napomene
- **Ubacivanje operatora i uslovi uspeha.** Kod SQL injekcije ubačeni znakovi menjaju tekst upita. Ovde najčešći oblik ne spaja tekst, nego podmeće objekat umesto očekivane vrednosti. Zato MongoDB u istom odgovoru navodi da tradicionalni napadi SQL injekcijom za njega nisu problem, ali to ne isključuje podmetanje operatora. Za to su potrebna tri uslova. Proizvod mora da primi strukturisan ulaz: JSON telo zahteva, ili parametre koje biblioteka za obradu zahteva pretvara u objekat. Biblioteka qs, na primer, parametar `foo[bar]=baz` pretvara u `{ foo: { bar: 'baz' } }`, pa `kod[$ne]=x` postaje objekat sa operatorom. Proizvod zatim mora da vrednost bez provere stavi u upit. Na kraju, odgovor mora da otkrije rezultat, bilo prikazom fakture, bilo samom razlikom između uspeha i neuspeha.
- **Ubacivanje JavaScript-a.** MongoDB navodi da `$where`, `mapReduce`, `$accumulator` i `$function` omogućavaju izvršavanje proizvoljnih JavaScript izraza na serveru baze. Ako proizvod u takav izraz ugradi tekst korisnika, ubačeni deo se izvršava kao JavaScript. To je bliže klasičnom ubacivanju u izraz nego podmetanju operatora. Od ovih mogućnosti, `mapReduce` je od verzije 5.0 označen kao zastareo.
- **Zaštita.**
  - Proverava se tip vrednosti: kod mora biti tekst, a ne objekat. Videti [[Validacija ulaza]].
  - MongoDB preporučuje da se za vrednosti koje dolaze od korisnika uvek koristi izričit oblik `{ polje: { $eq: vrednost } }`. Tada se vrednost poredi kao celina, a ne tumači kao operator.
  - Umesto `$where` koristi se `$expr`, koji ne izvršava JavaScript. Ako se izvršavanje JavaScript-a na serveru ne koristi, isključuje se podešavanjem `security.javascriptEnabled` ili opcijom `--noscripting`.
  - Biblioteka qs upozorava da je nebezbedno ulaz proveriti jednim parserom, a koristiti ga posle obrade drugim. Provera se radi nad istim objektom koji ulazi u upit.
- **Naziv.** „NoSQL“ je zbirni naziv za različite vrste baza i modela podataka, na primer [[Dokument-orijentisana baza podataka|dokument-orijentisane]] i [[Ključ-vrednost baza podataka|ključ-vrednost baze]], a ne naziv jednog upitnog jezika. Naziv ne znači da takve baze nikada nemaju jezik nalik SQL-u: dokumentacija baze Cassandra, na primer, navodi da njen jezik CQL nudi model sličan SQL-u. MITRE ne vodi poseban unos, nego „NoSQL Injection“ i „NoSQLi“ navodi kao alternativne nazive klase CWE-943, uz primere MongoDB, Cassandra, Elasticsearch i Redis. Mehanizmi i primeri u ovoj belešci odnose se na MongoDB i ne prenose se automatski na druge baze. [[Upitni jezik]] opisuje zašto naredbe ključ-vrednost baze po ključu ovde nisu upitni jezik.
- **Veza sa vrstom baze.** Mehanizam ubacivanja operatora već je opisan u delu **Komande** beleške [[Dokument-orijentisana baza podataka]]. Ova beleška ga imenuje kao napad i povezuje sa uslovima i zaštitama.
- **Ograničenje štete.** Proizvod pristupa bazi [[Servisni nalog|servisnim nalogom]]. Ako taj nalog sme samo da čita kolekciju faktura, napad iz primera i dalje otkriva fakture, ali ne može da menja druge kolekcije.
