---
tip: odluke
---
# Odluke

## Pretpostavljeni pojmovi
Pojmovi koje publika zna bez definisanja. Ne otvaraju se ponovo osim na zahtev studenta.

- organizacija, preduzeće, zaposleni, korisnik
- sistem (u opštem smislu), arhitektura softvera
- podatak, informacija, dokument, fajl
- aplikacija, web aplikacija, programski interfejs (API), HTTP zahtev i odgovor, HTTPS
- baza podataka, SQL upit
- server, operativni sistem, virtuelna mašina, oblak (cloud)
- računarska mreža, internet, ruter, mrežni preklopnik, Wi-Fi pristupna tačka, mrežni segment
- zaštitni zid (firewall), kao uređaj; njegova uloga u zaštiti opisuje se kroz [[Bezbednosna kontrola|bezbednosnu kontrolu]]
- izvorni kod, repozitorijum izvornog koda, softverska biblioteka, verzija softvera, testno okruženje, CI cevovod
- lozinka, nalog, prijava na sistem (u svakodnevnom smislu; autentifikacija se definiše kasnije)
- e-pošta, prilog, makro (kao funkcija Office paketa)

## Promene konvencija
- 2026-10-29: Temeljne definicije preuzete su sa predavanja ZOSS 03. Nabrajanja vrsta (osnovna bezbednosna svojstva, tipovi kontrola, poreklo ranjivosti) premeštena su iz definicije u Napomene, da definicije ne bi bile cirkularne preko beleški koje ih definišu.
- 2026-10-29: Frontmatter beleške pojma ima, pored polja iz šablona, polje `status` (`predavanje`: definicija sa predavanja; `predlog`: čeka potvrdu studenata; `prihvaćeno`: potvrđeno) i polje `sloj` (`temelj`, `jezgro`, `front`, prema kosturu teme).
- 2026-10-29: Glavni termini prate predavanja (resurs, dostupnost), a termini iz srpskog izdanja ISO/IEC 27000 (imovina, raspoloživost) stavljaju se u `aliases`.
- 2026-10-29: Konkretne ranjivosti primarnog konteksta vode se u beleški konteksta ([[Fakturis]], *Poznate ranjivosti*). Beleške pojmova opisuju slabosti, odnosno vrste ranjivosti.
- 2026-10-29: U definiciji Bezbednosne kontrole ispravljena je slovna greška sa predavanja („mehanizam ugrađenu“ u „mehanizam ugrađen“).

- 2026-11-03: Lokalni predlog revizije Nedinog izlaganja posle odbrane. Beleške se organizuju kroz obradu, prenos i čuvanje podataka. To su preseci analize, ne međusobno isključive vrste slabosti ni nova zamena za profesorove definicije. Svaki primer razdvaja resurs i zahtev, posmatranu komponentu, vrstu nedostatka i uslov pod kojim postoji konkretna ranjivost.
- 2026-11-03: U ovoj reviziji slabost označava vrstu nedostatka, a ranjivost konkretnu pojavu prema predavanju. Slabost nije događaj niti radnja napada. Pristup se ilustruje uslovnim scenarijima, ne popisom navodno potvrđenih ranjivosti Fakturisa.
- 2026-11-03: Slaba autentifikacija zamenjena je neispravnom autentifikacijom sa kriterijumom provere dokaza identiteta. Nezaštićen prenos razrađen je kao izostanak zaštite poverljivosti prenosa. Beleženje je odvojeno od praćenja. Dodati su provera integriteta, potrošnja resursa i opštija zaštita pristupnih podataka. Po izričitom Nedinom izboru, Injekcija, Prekomerno ovlašćenje i Ugrađeni pristupni podatak uklonjeni su iz ovog skupa za prvo izlaganje; ostaje osam beležaka opštijeg nivoa. Pogrešna konfiguracija uklonjena je kao zasebna glavna beleška; podešavanje može biti mesto nastanka pojedinačnih nedostataka.
- 2026-11-03: Po izričitom dogovoru sa Nedom, njegove beleške prate šablon sa samo `tip`, `aliases` i `izvor`, bez `status`, `sloj` i odeljka Kontraprimer. Ovaj dogovor za Nedin predlog ima prednost nad starijom stavkom o dodatnim poljima; nije izmena tuđih beležaka.

- 2026-11-03: Zaokružen Nedin lokalni skup za prvo izlaganje: Slabost kao uvod i sedam opštijih vrsta nedostataka. Vrsta komponente (obrada, prenos, čuvanje) i vrsta nedostatka dve su povezane ose analize, ne jedno stablo podvrsta. Primeri su poslovno neutralni scenariji, jer konkretna studija slučaja još može promeniti delatnost. Tačne tehnologije, protokoli i konkretni nalazi ostavljeni su za dalju razradu. Najava podele naredne sesije nije tretirana kao potvrđena konačna raspodela tima.

## Otvorena pitanja
- **Primarni kontekst.** Fakturis (aplikacija za izdavanje i naplatu faktura, sopstvena server soba, PayNet kao spoljni servis) je predlog. Potvrditi domen, naziv i odluku da su serveri lokalno, a ne u oblaku.
- **Slabost.** Lokalni predlog od 2026-11-03 koristi vrstu nedostatka i konkretnu ranjivost, prema beleškama sa odbrane. Uskladiti ovu terminološku odluku sa grupom i urednikom; ne tumačiti da nedostatak vremenski „postaje“ ranjivost tek kada se izvede napad.
- **Pretnje bez napadača.** Po definiciji sa predavanja, kvar, požar ili greška zaposlenog nisu pretnje. Da li su onda rezervne kopije, napajanje bez prekida i zaštita od požara bezbednosne kontrole, kada štite od događaja koji nisu pretnje? Pitanje za profesora.
- **„Događaj“ u definiciji pretnje.** Sada se koristi u svakodnevnom smislu. Kada se definiše pojam Događaj iz kostura (Događaj, incident i log), proveriti da li je to isto značenje.
- **Ovlašćenje, pravo pristupa, dozvola, privilegija.** Koriste se kao sinonimi. Ustaliti jedan termin kada se definiše kontrola pristupa. Konkretnija beleška o prekomernom ovlašćenju nije deo ovog prvog skupa.
- **Skeneri ranjivosti kao kontrola.** Da li su SAST, DAST i pentest detektivne kontrole (otkrivaju) ili preventivne (deluju pre napada)? Izvori se razlikuju.
- **Rizik.** Kostur ga stavlja u temelj, ali ga nema na dijagramu sa predavanja. Treba ga definisati pre prioritizacije ranjivosti (CVSS).
