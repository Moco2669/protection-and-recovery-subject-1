---
tip: odluke
---
# Odluke

## Pretpostavljeni pojmovi
Pojmovi koje publika zna bez definisanja. Ne otvaraju se ponovo osim na zahtev studenta.

- organizacija, preduzeće, korisnik
- sistem (u opštem smislu), arhitektura softvera
- podatak, informacija, dokument, fajl
- aplikacija (u opštem smislu), programski interfejs (API), HTTP zahtev i odgovor, HTTPS
- SQL upit
- računar, operativni sistem, virtuelna mašina, oblak (cloud)
- računarska mreža, internet, ruter, mrežni preklopnik, Wi-Fi pristupna tačka, mrežni segment
- zaštitni zid (firewall), kao uređaj
- izvorni kod, softverska biblioteka, verzija softvera, testno okruženje, CI cevovod
- lozinka, nalog, prijava na sistem (u svakodnevnom smislu; autentifikacija se definiše kasnije)
- e-pošta, prilog, makro (kao funkcija Office paketa)

### Pojmovi sa predavanja ZOSS 03
Definicije su preuzete sa predavanja *ZOSS 03: Osnovna terminologija pretnji*. Ova grana ih ne ponavlja kao beleške. Zatvorene su te definicije sa predavanja. Beleške podvrsta (konkretne ranjivosti, tipovi kontrola) time nisu zatvorene i ostaju na granama kolega.

- **Resurs (asset).** Resurs je sve što ima vrednost za organizaciju i što doprinosi ostvarenju njenih ciljeva. Može biti materijalan (na primer oprema, prostorije, ljudi) ili nematerijalan (na primer podaci, softver, usluge, poslovni procesi, reputacija). U srpskom izdanju ISO/IEC 27000 za *asset* koristi se „imovina“.
- **Bezbednosno svojstvo (security property).** Bezbednosno svojstvo je osobina resursa od koje zavisi njegova vrednost za organizaciju, a koju mogu da naruše nedozvoljene radnje nad resursom. Osnovna su poverljivost, integritet, dostupnost i neporecivost.
- **Poverljivost (confidentiality).** Poverljivost je bezbednosno svojstvo resursa da informacije koje sadrži nisu dostupne niti otkrivene licima, sistemima ili procesima koji za to nisu ovlašćeni.
- **Integritet (integrity).** Integritet je bezbednosno svojstvo resursa da je tačan i potpun, te da nije izmenjen ni uništen na nedozvoljen način.
- **Dostupnost (availability).** Dostupnost je bezbednosno svojstvo resursa da je pristupačan i upotrebljiv kada ga ovlašćeno lice ili sistem zatraži.
- **Neporecivost (non-repudiation).** Neporecivost je bezbednosno svojstvo resursa da se svaka radnja nad njim može pouzdano pripisati onome ko ju je izvršio, tako da on kasnije ne može uspešno da porekne da ju je izvršio.
- **Bezbednosni zahtev (security requirement).** Bezbednosni zahtev je pravilo koje za određeni resurs utvrđuje ko sme, a ko mora moći da izvrši koje radnje nad njim. Svaki bezbednosni zahtev konkretizuje neko bezbednosno svojstvo tog resursa.
- **Komponenta sistema (system component).** Komponenta sistema je deo sistema organizacije u kom se resurs skladišti, obrađuje, ili kroz koji se prenosi. Može biti softverska, hardverska ili mrežna, ali i ljudska ili fizička, kao zaposleni koji obrađuje podatke ili arhiva papirne dokumentacije.
- **Napadač (attacker).** Napadač je lice, grupa ili organizacija koja namerava da naruši bezbednosna svojstva resursa organizacije kao sredstvo za ostvarenje sopstvenog cilja. Taj cilj je motivacija napadača: finansijska korist, informacije, ideološki ili politički uticaj, osveta, lično zadovoljstvo ili prinuda.
- **Pretnja (threat).** Pretnja je mogući događaj u kom napadač narušava određeno bezbednosno svojstvo određenog resursa.
- **Pretnja po komponenti (component-level threat).** Pretnja po komponenti je pretnja ograničena na jednu komponentu sistema u kojoj se ugroženi resurs nalazi.
- **Ranjivost (vulnerability).** Ranjivost je osobina komponente sistema zbog koje komponenta omogućava radnju suprotnu nekom bezbednosnom zahtevu, a kojom napadač može da ostvari pretnju. Nastaje u dizajnu, implementaciji, konfiguraciji ili načinu upotrebe komponente.
- **Napad (attack).** Napad je niz radnji koje napadač izvodi ili navodi druge da izvedu, u pokušaju da ostvari jednu ili više pretnji po komponenti. U tom nizu napadač po potrebi iskorišćava ranjivosti komponenti da bi stekao mogućnosti koje nema, dok ne bude u stanju da naruši bezbednosno svojstvo ciljnog resursa.
- **Bezbednosna kontrola (security control).** Bezbednosna kontrola je mehanizam ugrađen u komponentu sistema ili posebna komponenta, kojom organizacija sprečava, otkriva ili ispravlja narušavanje bezbednosnih svojstava resursa. Može biti tehnička, organizaciona, kadrovska ili fizička.

## Promene konvencija
- 2026-10-29: Temeljne definicije preuzete su sa predavanja ZOSS 03. Nabrajanja vrsta (osnovna bezbednosna svojstva, tipovi kontrola, poreklo ranjivosti) premeštena su iz definicije u Napomene, da definicije ne bi bile cirkularne preko beleški koje ih definišu.
- 2026-10-29: Frontmatter beleške pojma ima, pored polja iz šablona, polje `status` (`predavanje`: definicija sa predavanja; `predlog`: čeka potvrdu studenata; `prihvaćeno`: potvrđeno) i polje `sloj` (`temelj`, `jezgro`, `front`, prema kosturu teme).
- 2026-10-29: Glavni termini prate predavanja (resurs, dostupnost), a termini iz srpskog izdanja ISO/IEC 27000 (imovina, raspoloživost) stavljaju se u `aliases`.
- 2026-10-29 (zamenjeno istog dana, vidi sledeću stavku): konkretne ranjivosti vode se u beleški konteksta, a beleške pojmova opisuju slabosti.
- 2026-10-29: **Promena po dogovoru sa studentima.** Prezentacije ne ponavljaju pojmove sa predavanja, nego uvode nove:
  - prezentacija 1 uvodi dvanaest konkretnih komponenti sistema kao pojmove (Zaposleni, Poslovni računar, Mrežni prolaz, Interna mreža, Server, Web aplikacija, Baza podataka, Skladište dokumenata, Repozitorijum izvornog koda, Sistem za upravljanje nalozima, Sistem za zapise o radu, Sistem za rezervne kopije). Zato zaposleni, web aplikacija, baza podataka, server i repozitorijum izvornog koda više nisu pretpostavljeni pojmovi;
  - prezentacija 2 uvodi ranjivosti tih komponenti. Ta odluka važi za rundu, ali beleške ranjivosti nisu na ovoj grani;
  - beleške Granica sistema, Tip komponente sistema, Tok podataka, Poslovni proces i Spoljni servis ostaju kao pomoćni pojmovi za opis arhitekture i ne ulaze u osnovni spisak prezentacije 1.
- 2026-10-29: Tabela konkretnih ranjivosti u beleški konteksta ([[Fakturis]], *Poznate ranjivosti*) grupisana je po komponentama. Prva ranjivost uz svaku komponentu je glavna.
- 2026-10-29: U definiciji Bezbednosne kontrole ispravljena je slovna greška sa predavanja („mehanizam ugrađenu“ u „mehanizam ugrađen“).
- 2026-10-30: `sazetak.txt` je uklonjen. Struktura firme živi u belešci konteksta [[Fakturis]]. `handoff.md` nije deo zajedničke baze na `main`. Ostaje na ličnim granama, za presek statusa.
- 2026-10-30: Resurs, komponenta sistema i ostali pojmovi sa predavanja ZOSS 03 nemaju beleške. Definicije stoje u Pretpostavljenim pojmovima, da bi modeli imali kontekst. Zatvorene su definicije sa predavanja. Beleške podvrsta ostaju na granama kolega.
- 2026-10-30: Prezentacija 1 uvodi deset konkretnih komponenti: Zaposleni, Poslovni računar, Mrežni prolaz, Interna mreža, Server, Web aplikacija, Baza podataka, Skladište dokumenata, Repozitorijum izvornog koda, Sistem za rezervne kopije. Korisnički podaci, fakture, poslovni dokumenti, izvorni kod i rezervne kopije su primeri resursa, ne zasebne beleške. PayNet nije komponenta sistema: servis je druge firme. Tok podataka, granica sistema i poslovni proces se na ovoj prezentaciji ne definišu. Beleške Sistema za upravljanje nalozima i Sistema za zapise o radu ostaju u bazi, ali nisu deo ove prezentacije.
- 2026-10-30: Sa ove grane obrisane su beleške ranjivosti (Podložnost socijalnom inženjeringu, Nedostatak segmentacije mreže, Slaba autentifikacija, Nezaštićena rezervna kopija). Pojmove za prezentaciju 2 radi kolega na svojoj grani. U [[Fakturis]] ostaje tabela konkretnih slabosti firme, bez linkova ka tim pojmovima.

## Otvorena pitanja
- **Primarni kontekst.** Fakturis (aplikacija za izdavanje i naplatu faktura, sopstvena server soba, PayNet kao spoljni servis) je predlog. Potvrditi domen, naziv i odluku da su serveri lokalno, a ne u oblaku.
- **Slabost.** Usvojena je šira formulacija, po kojoj je slabost nedostatak koji pod određenim okolnostima postaje ranjivost (CWE). Beleške nema na ovoj grani. Pitanje ostaje kolegi koji radi prezentaciju 2.
- **Fizičko okruženje.** Nije među dvanaest komponenti. U [[Fakturis]] opisano je posebno, van tih dvanaest. Ako se uključi kao trinaesta komponenta, treba definisati i nedostatak fizičke zaštite.
- **Pretnje bez napadača.** Po definiciji sa predavanja, kvar, požar ili greška zaposlenog nisu pretnje. Da li su onda rezervne kopije, napajanje bez prekida i zaštita od požara bezbednosne kontrole, kada štite od događaja koji nisu pretnje? Pitanje za profesora.
- **„Događaj“ u definiciji pretnje.** Sada se koristi u svakodnevnom smislu. Kada se definiše pojam Događaj iz kostura (Događaj, incident i log), proveriti da li je to isto značenje.
- **Ovlašćenje, pravo pristupa, dozvola, privilegija.** Koriste se kao sinonimi. Ustaliti jedan termin kada se definiše kontrola pristupa. Naziv „prekomerno ovlašćenje“ prirodniji je u množini, a beleška bi po konvenciji bila u jednini. Pojam nije na ovoj grani.
- **Skeneri ranjivosti kao kontrola.** Da li su SAST, DAST i pentest detektivne kontrole (otkrivaju) ili preventivne (deluju pre napada)? Izvori se razlikuju.
- **Rizik.** Kostur ga stavlja u temelj, ali ga nema na dijagramu sa predavanja. Treba ga definisati pre prioritizacije ranjivosti (CVSS).
