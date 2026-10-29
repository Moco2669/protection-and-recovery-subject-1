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
- zaštitni zid (firewall), kao uređaj; njegova uloga u zaštiti opisuje se kroz [[Bezbednosna kontrola|bezbednosnu kontrolu]]
- izvorni kod, softverska biblioteka, verzija softvera, testno okruženje, CI cevovod
- lozinka, nalog, prijava na sistem (u svakodnevnom smislu; autentifikacija se definiše kasnije)
- e-pošta, prilog, makro (kao funkcija Office paketa)

## Promene konvencija
- 2026-10-29: Temeljne definicije preuzete su sa predavanja ZOSS 03. Nabrajanja vrsta (osnovna bezbednosna svojstva, tipovi kontrola, poreklo ranjivosti) premeštena su iz definicije u Napomene, da definicije ne bi bile cirkularne preko beleški koje ih definišu.
- 2026-10-29: Frontmatter beleške pojma ima, pored polja iz šablona, polje `status` (`predavanje`: definicija sa predavanja; `predlog`: čeka potvrdu studenata; `prihvaćeno`: potvrđeno) i polje `sloj` (`temelj`, `jezgro`, `front`, prema kosturu teme).
- 2026-10-29: Glavni termini prate predavanja (resurs, dostupnost), a termini iz srpskog izdanja ISO/IEC 27000 (imovina, raspoloživost) stavljaju se u `aliases`.
- 2026-10-29 (zamenjeno istog dana, vidi sledeću stavku): konkretne ranjivosti vode se u beleški konteksta, a beleške pojmova opisuju slabosti.
- 2026-10-29: **Promena po dogovoru sa studentima.** Prezentacije ne ponavljaju pojmove sa predavanja, nego uvode nove:
  - prezentacija 1 uvodi dvanaest konkretnih komponenti sistema kao pojmove (Zaposleni, Poslovni računar, Mrežni prolaz, Interna mreža, Server, Web aplikacija, Baza podataka, Skladište dokumenata, Repozitorijum izvornog koda, Sistem za upravljanje nalozima, Sistem za zapise o radu, Sistem za rezervne kopije). Zato zaposleni, web aplikacija, baza podataka, server i repozitorijum izvornog koda više nisu pretpostavljeni pojmovi;
  - prezentacija 2 uvodi ranjivosti tih komponenti. Beleške ranjivosti se definišu kao vrsta [[Ranjivost|ranjivosti]] vezana za komponentu („X je ranjivost web aplikacije u kojoj...“), a ne kao [[Slabost|slabost]]. Slabost ostaje pomoćni pojam za razliku između ranjivosti i kataloga kao što su CWE i OWASP;
  - beleške Granica sistema, Tip komponente sistema, Tok podataka, Poslovni proces i Spoljni servis ostaju kao pomoćni pojmovi za opis arhitekture i ne ulaze u osnovni spisak prezentacije 1.
- 2026-10-29: Tabela konkretnih ranjivosti u beleški konteksta ([[Fakturis]], *Poznate ranjivosti*) grupisana je po komponentama. Prva ranjivost uz svaku komponentu je glavna.
- 2026-10-29: U definiciji Bezbednosne kontrole ispravljena je slovna greška sa predavanja („mehanizam ugrađenu“ u „mehanizam ugrađen“).

## Otvorena pitanja
- **Primarni kontekst.** Fakturis (aplikacija za izdavanje i naplatu faktura, sopstvena server soba, PayNet kao spoljni servis) je predlog. Potvrditi domen, naziv i odluku da su serveri lokalno, a ne u oblaku.
- **Slabost.** Usvojena je šira formulacija, po kojoj je slabost nedostatak koji pod određenim okolnostima postaje ranjivost (CWE). Pošto prezentacija 2 sada govori o ranjivostima, ovo pitanje je manje hitno. Ostaje da se odluči da li se pojam Slabost uopšte prikazuje u prvoj rundi.
- **Fizičko okruženje.** Nije među dvanaest komponenti, jer ga `sazetak.txt` navodi posebno. Ako se uključi kao trinaesta komponenta, treba definisati i [[Nedostatak fizičke zaštite]].
- **Pretnje bez napadača.** Po definiciji sa predavanja, kvar, požar ili greška zaposlenog nisu pretnje. Da li su onda rezervne kopije, napajanje bez prekida i zaštita od požara bezbednosne kontrole, kada štite od događaja koji nisu pretnje? Pitanje za profesora.
- **„Događaj“ u definiciji pretnje.** Sada se koristi u svakodnevnom smislu. Kada se definiše pojam Događaj iz kostura (Događaj, incident i log), proveriti da li je to isto značenje.
- **Ovlašćenje, pravo pristupa, dozvola, privilegija.** Koriste se kao sinonimi. Ustaliti jedan termin kada se definiše kontrola pristupa. Uz to: naziv beleške [[Prekomerno ovlašćenje]] je u jednini po konvenciji, iako je množina prirodnija.
- **Skeneri ranjivosti kao kontrola.** Da li su SAST, DAST i pentest detektivne kontrole (otkrivaju) ili preventivne (deluju pre napada)? Izvori se razlikuju.
- **Rizik.** Kostur ga stavlja u temelj, ali ga nema na dijagramu sa predavanja. Treba ga definisati pre prioritizacije ranjivosti (CVSS).
