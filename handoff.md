# Handoff: baza znanja bez pojmova

Stanje na dan 30. 10. 2026. Folder `pojmovi/` je ispražnjen na grani `main`.

## Šta je urađeno

Početna baza znanja (Obsidian vault u korenu) zadržava konfiguraciju i primarni kontekst. Sve beleške pojmova su uklonjene.

```
_meta/konfiguracija.md   tema, problem, publika, primarni kontekst
_meta/odluke.md          pretpostavljeni pojmovi, konvencije, otvorena pitanja
konteksti/Fakturis.md    primarni kontekst: firma, komponente, procesi, zahtevi, ranjivosti
pojmovi/                 prazan (36 beleški uklonjeno 30. 10. 2026.)
handoff.md               ovaj fajl
```

Ulazi koji su ranije korišćeni za izradu pojmova: `Tema 1 - Kostur.md`, `sazetak.txt` i predavanja ZOSS 01, 02 i 03 iz `Materijali/`.

**Primarni kontekst.** Firma *Fakturis d.o.o.* (oko 20 zaposlenih, Novi Sad) razvija web aplikaciju za izdavanje i naplatu faktura. Aplikacija čuva podatke korisnika i njihovih kupaca, a naplatu obavlja preko spoljnog platnog servisa *PayNet*. Struktura komponenti je preuzeta iz `sazetak.txt` (šest celina). Svi serveri su u sopstvenoj server sobi. Beleška konteksta i dalje sadrži tabelu bezbednosnih zahteva (resurs × svojstvo) i tabelu poznatih ranjivosti; wikilinkovi ka pojmovima trenutno vode na nepostojeće beleške.

**Pojmovi.** Nema. Folder `pojmovi/` je prazan. Prethodno je bilo 36 beleški (14 sa predavanja ZOSS 03 i 22 predloga za prve tri prezentacije); sve su obrisane sa `main`.

## Mapa za prvu rundu (3 × 10 minuta)

Mapa ispod ostaje kao orijentir za sadržaj prezentacija. Pojmovi koje navodi treba ponovo definisati u `pojmovi/` pre izlaganja.

### Prezentacija 1: komponente, arhitektura, poslovni procesi
- Kontekst: [[Fakturis]], odeljci *Resursi*, *Komponente sistema*, *Spoljni subjekti*, *Poslovni procesi*, *Glavni tokovi podataka*.
- Pojmovi za (ponovnu) definiciju: Resurs, Komponenta sistema, Tip komponente sistema, Granica sistema, Tok podataka, Poslovni proces, Spoljni servis.

### Prezentacija 2: konkretne ranjivosti
- Kontekst: [[Fakturis]], odeljci *Bezbednosni zahtevi* i *Poznate ranjivosti*.
- Pojmovi za (ponovnu) definiciju: Bezbednosno svojstvo (i četiri svojstva), Bezbednosni zahtev, Ranjivost, Slabost, Napadač, Pretnja, Pretnja po komponenti, Napad; slabosti: Neispravna kontrola pristupa, Injekcija, Nedovoljna provera autentičnosti podataka, Nekontrolisana učestalost zahteva, Ugrađeni pristupni podatak, Pogrešna bezbednosna konfiguracija, Nezakrpljen softver, Prekomerno ovlašćenje, Nedovoljno beleženje i praćenje.

### Prezentacija 3: tipovi bezbednosnih kontrola
- Pojmovi za (ponovnu) definiciju: Bezbednosna kontrola; po dejstvu Preventivna, Detektivna, Korektivna; po prirodi Tehnička, Organizaciona, Kadrovska, Fizička.

## Odluke koje čekaju potvrdu
Detalji su u `_meta/odluke.md`, odeljak *Otvorena pitanja*. Najvažnije su:
1. Da li prihvatate Fakturis kao primarni kontekst (domen, ime, serveri lokalno). Ako ne, menjati ga treba odmah, jer se sadržaj konteksta i budući primeri na njega oslanjaju.
2. Šira ili uža definicija slabosti. Utiče na drugu prezentaciju.
3. Pitanje za profesora: da li su kontrole protiv događaja bez napadača (kvar, požar) bezbednosne kontrole, kada po definiciji sa predavanja pretnja zahteva napadača.

## Sledeći koraci
1. **Ponovna izrada pojmova.** Kroz veštinu (`/baza-znanja`) definisati pojmove potrebne za prvu rundu prezentacija, počevši od temelja sa ZOSS 03.
2. **Uskladiti kontekst.** U [[Fakturis]] popraviti ili zameniti wikilinkove ka obrisanim pojmovima kada se beleške ponovo uvezu.
3. **Provera izvora.** Pre prezentacija proveriti CWE oznake i odredbe ISO/IEC 27002:2022 koje se citiraju.
4. **Rok za materijale.** Po predavanju ZOSS 02, materijali se šalju 48 sati pre sesije. Za grupe G3 i G4 rok je 1. 11., a sesija 3. 11. Proverite koja je vaša grupa.
5. **Kolege na drugim granama.** Posle ovog commit-a na `main`, kolege treba da urade `git fetch` i `git merge origin/main` (ili rebase) na svojoj grani da bi dobili prazan `pojmovi/` i ažuriran handoff.

## Napomene
- `_meta/` i `konteksti/Fakturis.md` nisu dirani u ovoj izmeni.
- `_meta/odluke.md` i dalje sadrži wikilinkove ka pojmovima koji više ne postoje; to treba uskladiti pri ponovnoj izradi pojmova.
