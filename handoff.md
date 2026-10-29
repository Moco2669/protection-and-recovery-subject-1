# Handoff: početna baza znanja

Stanje na dan 29. 10. 2026. Ništa nije komitovano u git.

## Šta je urađeno

Napravljena je početna baza znanja (Obsidian vault u korenu repozitorijuma) po veštini `baza-znanja`:

```
_meta/konfiguracija.md   tema, problem, publika, primarni kontekst
_meta/odluke.md          pretpostavljeni pojmovi, konvencije, otvorena pitanja
konteksti/Fakturis.md    primarni kontekst: firma, komponente, procesi, zahtevi, ranjivosti
pojmovi/                 36 beleški pojmova
handoff.md               ovaj fajl
```

Ulazi koji su korišćeni: `Tema 1 - Kostur.md`, `sazetak.txt` i predavanja ZOSS 01, 02 i 03 iz `Materijali/`.

**Primarni kontekst.** Firma *Fakturis d.o.o.* (oko 20 zaposlenih, Novi Sad) razvija web aplikaciju za izdavanje i naplatu faktura. Aplikacija čuva podatke korisnika i njihovih kupaca, a naplatu obavlja preko spoljnog platnog servisa *PayNet*. Struktura komponenti je preuzeta iz `sazetak.txt` (šest celina). Svi serveri su u sopstvenoj server sobi. Beleška konteksta sadrži i tabelu bezbednosnih zahteva (resurs × svojstvo) i tabelu 22 poznate ranjivosti. Svi primeri u bazi se na nju oslanjaju.

**Pojmovi** (polje `status` u frontmatter-u):
- 14 pojmova sa predavanja ZOSS 03 (`status: predavanje`), sa primerima iz Fakturisa: Resurs, Bezbednosno svojstvo, Poverljivost, Integritet, Dostupnost, Neporecivost, Bezbednosni zahtev, Komponenta sistema, Napadač, Pretnja, Pretnja po komponenti, Ranjivost, Napad, Bezbednosna kontrola.
- 22 nova pojma (`status: predlog`) za prve tri prezentacije, opisana u sledećem odeljku.

**Izvori.** Uz svaki pojam naveden je izvor sa najsličnijom definicijom. Proverene su oznake odredbi u ISO/IEC 27000:2018 (3.2, 3.7, 3.10, 3.28, 3.36, 3.48, 3.74, 3.77), definicije iz glosara NIST SP 800-53 Rev. 5 i lista OWASP Top 10:2025. Oznake CWE i odredbe ISO/IEC 27002:2022 navedene su po znanju i nisu proverene na izvoru, pa ih treba proveriti pre citiranja na prezentaciji.

## Mapa za prvu rundu (3 × 10 minuta)

### Prezentacija 1: komponente, arhitektura, poslovni procesi
- Kontekst: [[Fakturis]], odeljci *Resursi*, *Komponente sistema*, *Spoljni subjekti*, *Poslovni procesi*, *Glavni tokovi podataka* (sa mermaid dijagramom).
- Pojmovi: [[Resurs]], [[Komponenta sistema]], [[Tip komponente sistema]], [[Granica sistema]], [[Tok podataka]], [[Poslovni proces]], [[Spoljni servis]].
- Predlog toka: šta firma radi, zatim resursi, komponente po celinama i po tipu, granica sistema i PayNet, pa jedan proces (naplata fakture) praćen kroz komponente i tokove. Završiti tabelom bezbednosnih zahteva kao prelazom ka drugoj prezentaciji.

### Prezentacija 2: konkretne ranjivosti
- Kontekst: [[Fakturis]], odeljci *Bezbednosni zahtevi* i *Poznate ranjivosti*.
- Pojmovi: [[Bezbednosno svojstvo]] sa četiri svojstva, [[Bezbednosni zahtev]], [[Ranjivost]], [[Slabost]], [[Napadač]], [[Pretnja]], [[Pretnja po komponenti]], [[Napad]].
- Slabosti: [[Neispravna kontrola pristupa]], [[Injekcija]], [[Nedovoljna provera autentičnosti podataka]], [[Nekontrolisana učestalost zahteva]], [[Ugrađeni pristupni podatak]], [[Pogrešna bezbednosna konfiguracija]], [[Nezakrpljen softver]], [[Prekomerno ovlašćenje]], [[Nedovoljno beleženje i praćenje]].
- Predlog toka: razlika ranjivosti i slabosti, pa tri do četiri ranjivosti iz tabele, svaka od zahteva do ranjivosti. Kao završnicu prikazati napad ransomware grupe iz beleške [[Napad]], koji povezuje četiri ranjivosti u lanac.

### Prezentacija 3: tipovi bezbednosnih kontrola
- Pojmovi: [[Bezbednosna kontrola]]; po dejstvu [[Preventivna kontrola]], [[Detektivna kontrola]], [[Korektivna kontrola]]; po prirodi [[Tehnička kontrola]], [[Organizaciona kontrola]], [[Kadrovska kontrola]], [[Fizička kontrola]].
- Predlog toka: dve dimenzije klasifikacije (ISO/IEC 27002:2022 koristi iste), pa tabela iz [[Bezbednosna kontrola]] u kojoj je svaka kontrola odgovor na ranjivost iz druge prezentacije. Granične slučajeve (rezervna kopija kao korektivna, šifrovanje diska kao tehnička, gašenje naloga kao organizaciona) iskoristiti za diskusiju.

## Odluke koje čekaju potvrdu
Detalji su u `_meta/odluke.md`, odeljak *Otvorena pitanja*. Najvažnije su:
1. Da li prihvatate Fakturis kao primarni kontekst (domen, ime, serveri lokalno). Ako ne, menjati ga treba odmah, jer se svi primeri oslanjaju na njega.
2. Šira ili uža definicija [[Slabost|slabosti]]. Utiče na drugu prezentaciju.
3. Pitanje za profesora: da li su kontrole protiv događaja bez napadača (kvar, požar) bezbednosne kontrole, kada po definiciji sa predavanja pretnja zahteva napadača.

## Sledeći koraci
1. **Pregled predloga.** Svaki od tri prezentera pregleda beleške za svoju prezentaciju i kroz razgovor sa veštinom (`/baza-znanja`) potvrdi ili izmeni definicije. Prihvaćenim beleškama promeniti `status` u `prihvaćeno`.
2. **Pet slabosti bez beleške.** U tabeli ranjivosti linkovane su, a nisu definisane: [[Slaba autentifikacija]], [[Nedostatak segmentacije mreže]], [[Podložnost socijalnom inženjeringu]], [[Nezaštićena rezervna kopija]], [[Nedostatak fizičke zaštite]]. Definisati ih za drugu prezentaciju ili ih zameniti postojećim slabostima.
3. **Provera izvora.** Pre prezentacija proveriti CWE oznake i odredbe ISO/IEC 27002:2022 koje se citiraju.
4. **Rok za materijale.** Po predavanju ZOSS 02, materijali se šalju 48 sati pre sesije. Za grupe G3 i G4 rok je 1. 11., a sesija 3. 11. Proverite koja je vaša grupa. Predavanje ZOSS 01 navodi izlaganja od 12 do 15 minuta, a vi radite po 10. Ako dogovor sa profesorom nije zapisan, potvrdite trajanje.
5. **Naredne runde.** Sledeći pojmovi iz kostura po redosledu preduslova:
   - Rizik (potreban za CVSS i prioritizaciju);
   - Događaj, incident i log;
   - Identitet, autentifikacija, autorizacija i RBAC;
   - Socijalni inženjering, fišing, malver i zlonamerni dokumenti (makroi);
   - Kriptografija (heš, digitalni potpis), potrebna i za proveru potpisa PayNet obaveštenja;
   - Granica poverenja (trust boundary) i modelovanje pretnji;
   - Hardening, upravljanje konfiguracijom i tajnama, backup;
   - Lateral movement i privilege escalation, za koje napad ransomware grupe već daje primer.
6. **Presek stanja ili revizija.** Posle izmena zatražiti od veštine presek stanja ili reviziju, da bi se proverila cirkularnost, nepostojeći linkovi i usklađenost primera sa kontekstom.

## Napomene za nastavak rada
- Git status pre ovog rada pokazivao je da je `Tema 1 - Kostur.md` premešten iz `.claude/` u koren. Ta promena nije dirana.
- Definicije sa predavanja preuzete su skoro doslovno, uz dve izmene. Kod Bezbednosnog svojstva, Ranjivosti i Bezbednosne kontrole nabrajanja vrsta premeštena su u Napomene, da definicije ne bi bile cirkularne. U definiciji Bezbednosne kontrole ispravljena je slovna greška. Ako profesor očekuje doslovne formulacije, to su jedine razlike.
