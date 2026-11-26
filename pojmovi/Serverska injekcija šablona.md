---
tip: pojam
aliases: [server-side template injection, SSTI, injekcija šablona na serverskoj strani]
izvor: 'MITRE CWE-1336: https://cwe.mitre.org/data/definitions/1336.html; PortSwigger Web Security Academy, Server-side template injection: https://portswigger.net/web-security/server-side-template-injection; Kettle, Server-Side Template Injection, PortSwigger Research, 2015: https://portswigger.net/research/server-side-template-injection; OWASP Server Side Template Injection Prevention Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Template_Injection_Prevention_Cheat_Sheet.html'
status: predlog
sloj: jezgro
---
# Serverska injekcija šablona (server-side template injection)

## Definicija
Serverska injekcija šablona je [[Injekcioni napad|injekcioni napad]] u kome napadač ubacuje sintaksu jezika šablona u tekst koji komponenta predaje [[Mehanizam za šablone|mehanizmu za šablone]] kao šablon, a ne samo kao podatak, kako bi mehanizam na serveru izračunao izraze koje je napisao napadač i koje komponenta nije predvidela.

## Primer
U ilustrativnoj funkciji podsetnika, korisnik [[Fakturis|Fakturisa]] može da prilagodi tekst podsetnika za neplaćene fakture. Predviđeno je da u tekstu koristi samo četiri oznake za personalizaciju: `{{ kupac }}`, `{{ broj }}`, `{{ iznos }}` i `{{ rok }}`. Pretpostavimo da [[Softverski proizvod|proizvod]] koristi Jinja. U ranjivoj varijanti ceo korisnikov tekst, bez ikakvog ograničenja, postaje šablon:

```python
env.from_string(tekst_korisnika).render(kupac=kupac, broj=broj, iznos=iznos, rok=rok)
```

Napadač, prijavljen kao korisnik, u tekst upiše `{{ 7*7 }}` i u pregledu poruke vidi `49`. To što mehanizam obrađuje korisnikov tekst samo po sebi nije greška, jer je prilagođavanje podsetnika namerna funkcija. Rezultat `49` pokazuje nešto drugo: mehanizam je izračunao izraz koji nije nijedna od četiri predviđene oznake, pa korisnik može da piše bilo koji izraz jezika Jinja. Ranjivost je razlika između onoga što je proizvod nameravao da dozvoli i onoga što stvarno dozvoljava. Sam izraz `7*7` je bezopasan i ne dokazuje da napadač može da čita datoteke ili izvršava komande. Šta dalje može zavisi od mogućnosti mehanizma, objekata dostupnih iz šablona, eventualnih ograničenja sandbox režima i prava procesa proizvoda. U drugim mehanizmima ista proba ima drugačiju sintaksu, na primer `${7*7}`, pa napadač prvo utvrđuje koji se mehanizam koristi. Scenario je ilustracija, a ne potvrđena ranjivost Fakturisa.

Kontraprimer zavisi od toga šta korisnik treba da uređuje.

1. Ako korisnik uređuje samo podatak, na primer dodatnu rečenicu u poruci, proizvod koristi sopstveni, fiksni šablon, a korisnikov tekst predaje kao vrednost u kontekstu:

   ```python
   env.from_string(FIKSNI_SABLON).render(poruka=tekst_korisnika, kupac=kupac, iznos=iznos)
   ```

   Tekst `{{ 7*7 }}` se tada u poruci pojavljuje doslovno. To je obično umetanje korisničkog podatka u šablon, a ne injekcija šablona.
2. Ako korisnik treba da uređuje ceo tekst sa oznakama, fiksni šablon bi ukinuo funkciju. Tada proizvod dozvoljava samo predviđene oznake. Može sam da zameni tačno te četiri oznake vrednostima, bez predaje teksta mehanizmu Jinja, ili da pre obrade odbije svaki tekst sa bilo kojom drugom oznakom. U oba slučaja `{{ 7*7 }}` se ne izračunava.

## Napomene
- **Šablon ili podatak.** Suština napada je u tome šta komponenta predaje kao šablon. Razlika između šablona i konteksta objašnjena je u belešci [[Mehanizam za šablone]]. PortSwigger navodi da je unos bezbedan kada se samo prosledi šablonu kao podatak, a opasan kada se spoji sa šablonom ili sam postane šablon.
- **Uslovi.** Napad je moguć kada tekst iz [[Nepouzdan ulaz|nepouzdanog izvora]] postane deo šablona, kada mehanizam izračunava izraze izvan onoga što funkcija predviđa, nad objektima kojima napadač tako dobija pristup, i kada se rezultat ili njegovi efekti mogu uočiti. Sintaksa i mogućnosti zavise od konkretnog mehanizma.
- **Namerno uređivanje šablona.** Kettle navodi da injekcija šablona nastaje i greškom programera i namernim izlaganjem šablona radi bogatije funkcionalnosti, što je uobičajeno kod wiki sistema, blogova, marketinških aplikacija i sistema za upravljanje sadržajem. PortSwigger navodi i da neki sajtovi namerno dozvoljavaju privilegovanim korisnicima, na primer urednicima sadržaja, da uređuju šablone. Podsetnik Fakturisa je takav slučaj. Tada pitanje nije da li korisnik piše šablon, nego koliko jezika šablona sme da koristi.
- **Posledice.** PortSwigger navodi da napadač potencijalno može da postigne izvršavanje proizvoljnog koda i preuzme potpunu kontrolu nad serverom, ali i da domet zavisi od mehanizma, a da u retkim slučajevima ranjivost nema stvaran bezbednosni rizik. Izraz se izvršava sa pravima procesa proizvoda, pa domet određuju i prava [[Servisni nalog|servisnog naloga]] i [[Sistemsko okruženje|sistemsko okruženje]]. Kada isti proces služi sve korisnike, napad jednog korisnika ugrožava podatke svih.
- **Zaštita.** Mera zavisi od toga šta funkcija treba da omogući.
  - Kada korisnik uređuje samo podatak, primenjuje se fiksni šablon, a korisnikov tekst se predaje kao vrednost u kontekstu ([[Parametrizacija]]). OWASP preporučuje da se šabloni drže uz izvorni kod aplikacije i da se nikada ne grade od nepouzdanih podataka.
  - Kada korisnik uređuje ograničen šablon, proizvod proverava da tekst sadrži samo dozvoljene oznake ([[Validacija ulaza]]) ili ih sam zamenjuje. To je provera prema listi dozvoljenog, a ne uklanjanje „opasne“ sintakse, jer OWASP savetuje da se sintaksa šablona ne pokušava filtrirati iz ulaza.
  - Kada je potreban bogatiji jezik, PortSwigger i OWASP preporučuju najslabiji mehanizam koji je dovoljan, na primer Mustache bez logike. Druga mogućnost je ograničen režim, u Jinja-i `SandboxedEnvironment`. Jinja ipak navodi da sam sandbox nije rešenje za savršenu bezbednost i savetuje da se šablonu predaju samo potrebni podaci i da se ograniče resursi kao procesor i memorija. PortSwigger dodaje da je izvršavanje nepouzdanog koda u sandboxu teško i podložno zaobilaženju.
  - Dopunske mere: obrada šablona u zaključanom [[Kontejner|kontejneru]] (PortSwigger) i, prema OWASP-u, uređivanje šablona samo za ovlašćene uloge, uz evidenciju izmena.
- **Razlika od XSS-a.** Ako proizvod korisnikov tekst bez kodiranja ubaci u HTML stranicu, izvršavanje se dešava u pregledaču posetioca. To je druga vrsta napada. Kod SSTI izraz izračunava server, u [[Procesna jedinica|procesnoj jedinici]] proizvoda.
- **Mesto u klasifikaciji.** CWE-1336 je podvrsta CWE-94 (Improper Control of Generation of Code, alternativni naziv „Code Injection“). Ubačeni kod je ovde izraz jezika šablona, koji izračunava mehanizam za šablone, a ne mašinske instrukcije. CWE-1336 kao alternativne nazive navodi i SSTI i klijentsku varijantu (CSTI), pa „template injection“ bez odrednice obuhvata obe.
