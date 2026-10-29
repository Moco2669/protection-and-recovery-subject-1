# Handoff: početna baza znanja

Stanje na dan 29. 10. 2026. Ništa nije komitovano u git.

## Šta je urađeno

Napravljena je početna baza znanja (Obsidian vault u korenu repozitorijuma) po veštini `baza-znanja`:

```
_meta/konfiguracija.md   tema, problem, publika, primarni kontekst
_meta/odluke.md          pretpostavljeni pojmovi, konvencije, otvorena pitanja
konteksti/Fakturis.md    primarni kontekst: firma, komponente, procesi, zahtevi, ranjivosti
pojmovi/                 52 beleške pojmova
handoff.md               ovaj fajl
```

Ulazi koji su korišćeni: `Tema 1 - Kostur.md`, `sazetak.txt` i predavanja ZOSS 01, 02 i 03 iz `Materijali/`.

**Primarni kontekst.** Firma *Fakturis d.o.o.* (oko 20 zaposlenih, Novi Sad) razvija web aplikaciju za izdavanje i naplatu faktura. Aplikacija čuva podatke korisnika i njihovih kupaca, a naplatu obavlja preko spoljnog platnog servisa *PayNet*. Dvanaest komponenti preuzeto je iz `sazetak.txt`. Svi serveri su u sopstvenoj server sobi. Beleška konteksta sadrži i tabelu bezbednosnih zahteva (resurs × svojstvo) i tabelu konkretnih ranjivosti grupisanih po komponentama. Svi primeri u bazi se na nju oslanjaju.

**Pojmovi** (polje `status` u frontmatter-u):

| Grupa | Broj | Status |
|---|---|---|
| pojmovi sa predavanja ZOSS 03 | 14 | `predavanje` |
| konkretne komponente sistema (prezentacija 1) | 12 | `predlog` |
| ranjivosti komponenti (prezentacija 2) | 13 | `predlog` |
| tipovi bezbednosnih kontrola (prezentacija 3) | 7 | `predlog` |
| pomoćni pojmovi: Granica sistema, Tip komponente sistema, Tok podataka, Poslovni proces, Spoljni servis, Slabost | 6 | `predlog` |

**Izvori.** Uz svaki pojam naveden je izvor sa najsličnijom definicijom. Proverene su oznake odredbi u ISO/IEC 27000:2018, definicije iz glosara NIST SP 800-53 Rev. 5 i NIST CSRC (backup, social engineering, internal network), glosar CIS Controls v8 (end-user devices, network devices, servers, database, application, authentication systems) i lista OWASP Top 10:2025. Oznake CWE, odredbe ISO/IEC 27002:2022 i NIST SP 800-218 navedene su po znanju i nisu proverene na izvoru.

## Mapa za prvu rundu (3 × 10 minuta)

Pojmovi sa predavanja (resurs, komponenta sistema, ranjivost, bezbednosna kontrola i ostali) se ne prezentuju ponovo, samo se na njih poziva.

### Prezentacija 1: komponente i arhitektura sistema
Dvanaest konkretnih komponenti, po celinama iz `sazetak.txt`:

| Celina | Komponente |
|---|---|
| ljudi i radno okruženje | [[Zaposleni]], [[Poslovni računar]] |
| mreža i komunikacija | [[Mrežni prolaz]], [[Interna mreža]] |
| aplikacija i serversko okruženje | [[Server]], [[Web aplikacija]] (uključuje vezu sa PayNet-om) |
| čuvanje podataka | [[Baza podataka]], [[Skladište dokumenata]] |
| razvoj i održavanje | [[Repozitorijum izvornog koda]] (uz CI i testno okruženje) |
| zajedničke funkcije zaštite i podrške | [[Sistem za upravljanje nalozima]], [[Sistem za zapise o radu]], [[Sistem za rezervne kopije]] |

- Za arhitekturu: dijagram i tokovi podataka u [[Fakturis]], odeljak *Glavni tokovi podataka*. Pomoćni pojmovi [[Granica sistema]] i [[Tok podataka]] mogu se pomenuti u jednoj rečenici, bez posebnog izlaganja.
- Predlog toka: firma i njeni resursi u jednom slajdu, zatim šest celina sa po dve komponente (definicija i kako izgleda u Fakturisu), pa dijagram arhitekture. Završiti putem jedne fakture kroz komponente, kao prelaz ka ranjivostima.

### Prezentacija 2: ranjivosti tih komponenti
Osnovni spisak: po jedna glavna ranjivost za svaku od dvanaest komponenti. To je dvanaest konkretnih ranjivosti, koje pripadaju u deset vrsta.

| Komponenta | Glavna ranjivost u Fakturisu | Vrsta |
|---|---|---|
| Zaposleni | Jelena otvara priloge bez provere pošiljaoca | [[Podložnost socijalnom inženjeringu]] |
| Poslovni računar | makroi iz dokumenata sa interneta su dozvoljeni | [[Pogrešna bezbednosna konfiguracija]] |
| Mrežni prolaz | administratorski panel sa interneta, fabrička lozinka | [[Pogrešna bezbednosna konfiguracija]] |
| Interna mreža | računari, serveri i Wi-Fi za posetioce u istom segmentu | [[Nedostatak segmentacije mreže]] |
| Server | Ubuntu i nginx nisu ažurirani od marta | [[Nezakrpljen softver]] |
| Web aplikacija | `/api/fakture/{id}` ne proverava vlasništvo (IDOR) | [[Neispravna kontrola pristupa]] |
| Baza podataka | aplikacija se povezuje kao vlasnik baze | [[Prekomerno ovlašćenje]] |
| Skladište dokumenata | svi zaposleni čitaju i pišu ceo deljeni folder | [[Prekomerno ovlašćenje]] |
| Repozitorijum izvornog koda | API ključ za PayNet u `config/paynet.yml` | [[Ugrađeni pristupni podatak]] |
| Sistem za upravljanje nalozima | prijava samo lozinkom, procurela lozinka administratora | [[Slaba autentifikacija]] |
| Sistem za zapise o radu | ne beleže se prijave ni storniranja, zapisi se ne pregledaju | [[Nedovoljno beleženje i praćenje]] |
| Sistem za rezervne kopije | kopije dostupne iz iste mreže, nešifrovane, neprobane | [[Nezaštićena rezervna kopija]] |

- Dodatne ranjivosti web aplikacije, ako ima vremena: [[Nedovoljna provera autentičnosti podataka]] (lažno obaveštenje o uplati) i [[Nekontrolisana učestalost zahteva]] (provera ukradenih kartica preko PayNet-a). Obe direktno odgovaraju delu problema iz kostura o zloupotrebi tuđih API-ja, pa preporučujem da se bar jedna uključi. [[Injekcija]] je takođe opisana.
- Predlog toka: za svaku ranjivost reći koji zahtev krši i šta napadač time dobija. Završiti napadom ransomware grupe iz beleške [[Napad]], koji spaja ranjivosti zaposlenog, poslovnog računara, interne mreže i rezervnih kopija u jedan lanac.

### Prezentacija 3: tipovi bezbednosnih kontrola
- Pojmovi: po dejstvu [[Preventivna kontrola]], [[Detektivna kontrola]], [[Korektivna kontrola]]; po prirodi [[Tehnička kontrola]], [[Organizaciona kontrola]], [[Kadrovska kontrola]], [[Fizička kontrola]].
- Predlog toka: dve dimenzije klasifikacije (ISO/IEC 27002:2022 koristi iste), pa za nekoliko ranjivosti iz druge prezentacije pokazati kontrolu svakog tipa. Granične slučajeve (rezervna kopija kao korektivna, šifrovanje diska kao tehnička, gašenje naloga kao organizaciona) iskoristiti za diskusiju.

## Odluke koje čekaju potvrdu
Detalji su u `_meta/odluke.md`, odeljak *Otvorena pitanja*. Najvažnije su:
1. Da li prihvatate Fakturis kao primarni kontekst (domen, ime, serveri lokalno). Ako ne, menjati ga treba odmah, jer se svi primeri oslanjaju na njega.
2. Da li fizičko okruženje (server soba) ulazi kao trinaesta komponenta. Sada nije među dvanaest.
3. Pitanje za profesora: da li su kontrole protiv događaja bez napadača (kvar, požar) bezbednosne kontrole, kada po definiciji sa predavanja pretnja zahteva napadača.

## Sledeći koraci
1. **Pregled predloga.** Svaki od tri prezentera pregleda beleške za svoju prezentaciju i kroz razgovor sa veštinom (`/baza-znanja`) potvrdi ili izmeni definicije. Prihvaćenim beleškama promeniti `status` u `prihvaćeno`.
2. **Provera izvora.** Pre prezentacija proveriti CWE oznake i odredbe ISO/IEC 27002:2022 koje se citiraju.
3. **Rok za materijale.** Po predavanju ZOSS 02, materijali se šalju 48 sati pre sesije. Za grupe G3 i G4 rok je 1. 11., a sesija 3. 11. Proverite koja je vaša grupa. Predavanje ZOSS 01 navodi izlaganja od 12 do 15 minuta, a vi radite po 10. Ako dogovor sa profesorom nije zapisan, potvrdite trajanje.
4. **Naredne runde.** Sledeći pojmovi iz kostura, po redosledu preduslova:
   - Rizik (potreban za CVSS i prioritizaciju ranjivosti);
   - Događaj, incident i log;
   - Identitet, autentifikacija, autorizacija i RBAC;
   - Socijalni inženjering, fišing, malver i zlonamerni dokumenti (makroi);
   - Kriptografija (heš, digitalni potpis), potrebna i za proveru potpisa PayNet obaveštenja;
   - Granica poverenja (trust boundary) i modelovanje pretnji;
   - Hardening, upravljanje konfiguracijom i tajnama, backup;
   - Lateral movement i privilege escalation, za koje napad ransomware grupe već daje primer.
5. **Presek stanja ili revizija.** Posle izmena zatražiti od veštine presek stanja ili reviziju, da bi se proverila cirkularnost, nepostojeći linkovi i usklađenost primera sa kontekstom.

## Napomene za nastavak rada
- Git status pre ovog rada pokazivao je da je `Tema 1 - Kostur.md` premešten iz `.claude/` u koren. Ta promena nije dirana.
- Definicije sa predavanja preuzete su skoro doslovno, uz dve izmene. Kod Bezbednosnog svojstva, Ranjivosti i Bezbednosne kontrole nabrajanja vrsta premeštena su u Napomene, da definicije ne bi bile cirkularne. U definiciji Bezbednosne kontrole ispravljena je slovna greška.
- Jedini link bez beleške je [[Nedostatak fizičke zaštite]], u tabeli ranjivosti uz fizičko okruženje.
