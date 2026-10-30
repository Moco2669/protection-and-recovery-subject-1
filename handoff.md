# Handoff: presek posle spajanja sa main

Stanje na dan 30. 10. 2026. Grana `moco-branch` spojena je sa `origin/main` (commiti „Uklonjeni pojmovi” i „Uklanjanje handoff-a i sažetka”).

## Šta je urađeno

Na `main` su obrisane sve beleške iz `pojmovi/` koje su postojale u početnoj bazi, da bi se pojmovi radili iz početka. Ova grana je posle toga, u commitu „Revidirane komponente sistema”, izmenila deo tih beleški i dodala nove.

Pri spajanju prihvaćeno je brisanje svega što je `main` obrisao, uključujući 13 beleški koje je ova grana menjala. Zadržano je 16 beleški koje postoje samo na ovoj grani. Izmene u `konteksti/Fakturis.md` i `_meta/odluke.md` ostaju sa ove grane, jer `main` te fajlove nije dirao.

```
_meta/konfiguracija.md   tema, problem, publika, primarni kontekst
_meta/odluke.md          verzija sa ove grane; deo linkova vodi na obrisane beleške
konteksti/Fakturis.md    verzija sa ove grane; tabela ranjivosti linkuje i obrisane beleške
pojmovi/                 16 beleški (12 komponenti i 4 ranjivosti)
handoff.md               ovaj fajl
```

Ulazi koji su ranije korišćeni za izradu pojmova: `Tema 1 - Kostur.md` i predavanja ZOSS 01, 02 i 03 iz `Materijali/`. `sazetak.txt` je uklonjen 30. 10. 2026. Struktura firme je u [[Fakturis]].

**Primarni kontekst.** Firma *Fakturis d.o.o.* (oko 20 zaposlenih, Novi Sad) razvija web aplikaciju za izdavanje i naplatu faktura. Aplikacija čuva podatke korisnika i njihovih kupaca, a naplatu obavlja preko spoljnog platnog servisa *PayNet*. Dvanaest komponenti opisano je u [[Fakturis]]. Svi serveri su u sopstvenoj server sobi. Beleška konteksta sadrži tabelu bezbednosnih zahteva (resurs × svojstvo) i tabelu konkretnih ranjivosti grupisanih po komponentama.

**Pojmovi koji ostaju** (sve su `status: predlog`):

| Grupa | Beleške | Sloj |
|---|---|---|
| konkretne komponente | [[Zaposleni]], [[Poslovni računar]], [[Mrežni prolaz]], [[Interna mreža]], [[Server]], [[Web aplikacija]], [[Baza podataka]], [[Skladište dokumenata]], [[Repozitorijum izvornog koda]], [[Sistem za upravljanje nalozima]], [[Sistem za zapise o radu]], [[Sistem za rezervne kopije]] | `temelj` |
| ranjivosti dodate na ovoj grani | [[Podložnost socijalnom inženjeringu]], [[Nedostatak segmentacije mreže]], [[Slaba autentifikacija]], [[Nezaštićena rezervna kopija]] | `jezgro` |

**Uklonjeno sa maina, pa i sa ove grane.** 36 beleški početne baze: 14 pojmova sa predavanja ZOSS 03, 9 ranjivosti koje je ova grana bila izmenila (Injekcija, Nedovoljna provera autentičnosti podataka, Nedovoljno beleženje i praćenje, Neispravna kontrola pristupa, Nekontrolisana učestalost zahteva, Nezakrpljen softver, Pogrešna bezbednosna konfiguracija, Prekomerno ovlašćenje, Ugrađeni pristupni podatak), 7 tipova bezbednosnih kontrola i 6 pomoćnih pojmova (Granica sistema, Tip komponente sistema, Tok podataka, Poslovni proces, Spoljni servis, Slabost). Komponenta sistema, Ranjivost i Resurs su među obrisanima.

**Linkovi ka nepostojećim beleškama.** Svaka od 16 zadržanih beleški u definiciji koristi bar jedan obrisan pojam. Najčešće su to [[Komponenta sistema]], [[Ranjivost]] i [[Resurs]]. [[Fakturis]] u tabeli *Poznate ranjivosti* i dalje linkuje obrisane vrste ranjivosti, i [[Nedostatak fizičke zaštite]], koja ni ranije nije imala belešku. `_meta/odluke.md` linkuje [[Bezbednosna kontrola]], [[Ranjivost]], [[Slabost]], [[Prekomerno ovlašćenje]] i [[Nedostatak fizičke zaštite]].

## Mapa za prvu rundu (3 × 10 minuta)

### Prezentacija 1: komponente i arhitektura sistema
Dvanaest konkretnih komponenti i dalje ima beleške, po celinama iz [[Fakturis]]:

| Celina | Komponente |
|---|---|
| ljudi i radno okruženje | [[Zaposleni]], [[Poslovni računar]] |
| mreža i komunikacija | [[Mrežni prolaz]], [[Interna mreža]] |
| aplikacija i serversko okruženje | [[Server]], [[Web aplikacija]] |
| čuvanje podataka | [[Baza podataka]], [[Skladište dokumenata]] |
| razvoj i održavanje | [[Repozitorijum izvornog koda]] |
| zajedničke funkcije zaštite i podrške | [[Sistem za upravljanje nalozima]], [[Sistem za zapise o radu]], [[Sistem za rezervne kopije]] |

Arhitektura i tokovi podataka ostaju u [[Fakturis]], odeljak *Glavni tokovi podataka*. Pojmovi kojima se te komponente definišu (Komponenta sistema, Resurs, Granica sistema, Tok podataka, Tip komponente sistema, Poslovni proces, Spoljni servis) nemaju beleške i treba ih ponovo definisati pre izlaganja, ili iz definicija komponenti izbaciti.

### Prezentacija 2: ranjivosti tih komponenti
Tabela u [[Fakturis]], odeljak *Poznate ranjivosti*, i dalje je spisak primera. Od vrsta ranjivosti belešku imaju samo četiri:

| Komponenta | Glavna ranjivost u Fakturisu | Beleška |
|---|---|---|
| Zaposleni | Jelena otvara priloge bez provere pošiljaoca | [[Podložnost socijalnom inženjeringu]] |
| Interna mreža | računari, serveri i Wi-Fi za posetioce u istom segmentu | [[Nedostatak segmentacije mreže]] |
| Sistem za upravljanje nalozima | prijava samo lozinkom, procurela lozinka administratora | [[Slaba autentifikacija]] |
| Sistem za rezervne kopije | kopije dostupne iz iste mreže, nešifrovane, neprobane | [[Nezaštićena rezervna kopija]] |

Ostale vrste iz tabele (Pogrešna bezbednosna konfiguracija, Nezakrpljen softver, Neispravna kontrola pristupa, Prekomerno ovlašćenje, Ugrađeni pristupni podatak, Nedovoljno beleženje i praćenje, Injekcija, Nedovoljna provera autentičnosti podataka, Nekontrolisana učestalost zahteva) treba ponovo definisati. Isto važi za Ranjivost, Slabost, Bezbednosni zahtev, Napad i Napadač, jer se preostale beleške ranjivosti na njih oslanjaju.

### Prezentacija 3: tipovi bezbednosnih kontrola
Beleški nema. Ponovo definisati: Bezbednosna kontrola; po dejstvu Preventivna, Detektivna, Korektivna; po prirodi Tehnička, Organizaciona, Kadrovska, Fizička.

## Odluke koje čekaju potvrdu
Detalji su u `_meta/odluke.md`, odeljak *Otvorena pitanja*. Najvažnije su:
1. Da li prihvatate Fakturis kao primarni kontekst (domen, ime, serveri lokalno).
2. Da li fizičko okruženje (server soba) ulazi kao trinaesta komponenta. Sada nije među dvanaest. Ako da, treba beleška Nedostatak fizičke zaštite.
3. Pitanje za profesora: da li su kontrole protiv događaja bez napadača (kvar, požar) bezbednosne kontrole, kada po definiciji sa predavanja pretnja zahteva napadača.

Odluka o širem pojmu Slabost ostaje zapisana, ali beleška Slabost više ne postoji.

## Sledeći koraci
1. **Temelj pre ostatka.** Zadržane definicije nisu samostalne. Prvo ponovo definisati Komponenta sistema, Resurs i Ranjivost, ili preformulisati 16 beleški tako da te pojmove ne koriste.
2. **Vrste ranjivosti i kontrole.** Vratiti beleške potrebne za drugu i treću prezentaciju, pa u [[Fakturis]] i `_meta/odluke.md` srediti linkove koji sada vode u prazno.
3. **Provera izvora.** Pre prezentacija proveriti CWE oznake i odredbe ISO/IEC 27002:2022 koje se citiraju u zadržanim beleškama.
4. **Rok za materijale.** Po predavanju ZOSS 02, materijali se šalju 48 sati pre sesije. Za grupe G3 i G4 rok je 1. 11., a sesija 3. 11. Proverite koja je vaša grupa.

## Napomene
- Ovaj fajl nije ni verzija sa `main` ni verzija sa grane pre spajanja. `main` opisuje prazan `pojmovi/`. Grana pre spajanja opisuje 52 beleške.
- `_meta/konfiguracija.md` nije menjana ni na `main` ni na ovoj grani posle početne baze.
- `handoff.md` ostaje samo na ovoj grani, za lični presek statusa. Na `main` je uklonjen. `sazetak.txt` je uklonjen i ovde i na `main`.
