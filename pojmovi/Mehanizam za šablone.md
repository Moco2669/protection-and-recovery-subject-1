---
tip: pojam
aliases: [template engine, šablonski mehanizam]
izvor: 'PortSwigger Web Security Academy, Server-side template injection: https://portswigger.net/web-security/server-side-template-injection; Jinja dokumentacija: https://jinja.palletsprojects.com/en/stable/; Mustache, mustache(5): https://mustache.github.io/mustache.5.html'
status: predlog
sloj: temelj
---
# Mehanizam za šablone (template engine)

## Definicija
Mehanizam za šablone je softverska komponenta koja obrađuje šablon, unapred zapisan tekst ili dokument sa oznakama na mestima promenljivog sadržaja, zajedno sa podacima koje joj program preda, i iz njih proizvodi izlazni tekst ili dokument.

## Primer
U ilustrativnoj funkciji podsetnika za neplaćene fakture, [[Softverski proizvod|softverski proizvod]] [[Fakturis|Fakturisa]] koristi šablon zapisan u sintaksi mehanizma Jinja:

```
Poštovani {{ kupac }}, faktura {{ broj }} na iznos {{ iznos }} RSD dospela je {{ rok }}.
```

i podatke `kupac = "Mesara Zlatibor"`, `broj = "2026-117"`, `iznos = 12000`, `rok = "15. 11. 2026."`. Mehanizam najpre parsira šablon i u njemu prepoznaje nepromenljivi tekst i četiri izraza između `{{` i `}}`. Zatim svaki izraz izračunava nad prosleđenim podacima i rezultat umeće u tekst e-poruke. Šablon određuje oblik poruke, a podaci njen promenljivi sadržaj.

Kontraprimer: kod koji poruku sastavlja neposredno, spajanjem nepromenljivih delova teksta i vrednosti, na primer `"Poštovani " + kupac + ", faktura " + broj + " ..."`, ne koristi mehanizam za šablone. Oblik poruke zapisan je u samom programskom kodu, a ne u zasebnom šablonu koji neka komponenta obrađuje tokom rada, pa ne postoje ni oznake ni jezik šablona koje bi trebalo tumačiti.

## Napomene
- **Šablon, oznake i kontekst.** Šablon je tekst koji mehanizam parsira prema pravilima jezika šablona. Jinja dokumentacija navodi da šablon sadrži promenljive ili izraze, koji se pri obradi zamenjuju vrednostima, i oznake koje upravljaju logikom šablona. U Jinja sintaksi `{{ … }}` označava izraz čiji se rezultat upisuje u izlaz, a `{% … %}` naredbu, na primer uslov ili petlju. Podaci koje program preda čine kontekst: Jinja dokumentacija navodi da promenljive šablona definiše rečnik konteksta koji se predaje šablonu. Vrednosti iz konteksta mehanizam ne parsira kao šablon, nego ih samo koristi pri obradi oznaka. Zato isti tekst ima različito značenje zavisno od toga da li je deo šablona ili vrednost u kontekstu. Na toj razlici zasniva se [[Serverska injekcija šablona|serverska injekcija šablona]].
- **Odakle dolazi šablon.** Program šablon obično učitava iz datoteke, ali ga može napraviti i iz teksta tokom rada. U Jinja-i to radi `Environment.from_string()`, a izlaz se dobija pozivom `render()` sa vrednostima konteksta. Šablon napravljen iz teksta koji je uneo korisnik je [[Nepouzdan ulaz|nepouzdan ulaz]], iako izgleda kao deo programa.
- **Izražajnost jezika.** Mehanizmi se razlikuju po tome šta oznake u šablonu mogu da urade. Najjednostavnija obrada samo zamenjuje zatvoren skup oznaka vrednostima. Mustache sebe opisuje kao „logic-less templates“ i navodi da nema naredbi `if` i `else` ni petlji, nego samo oznake. Jinja, s druge strane, dozvoljava izraze, računske operacije, pristup atributima promenljivih iz konteksta, na primer `{{ kupac.naziv }}`, i naredbe. Drugi mehanizmi, kao Twig i FreeMarker, imaju sopstvene jezike i sintaksu. Što je jezik izražajniji, više može onaj ko piše šablon.
- **Mehanizam kao interpreter.** Mehanizam koji podržava izraze i naredbe izvršava ih tokom rada programa, pa se prema jeziku šablona ponaša kao [[Interpreter|interpreter]]. Način izvršavanja se razlikuje. Jinja dokumentacija navodi da Jinja šablon kompajlira u Python kod i taj kod čuva, da ga ne bi parsirala i tumačila pri svakoj obradi. To je i dalje izvršavanje međuoblika teksta primljenog tokom rada, kako je opisano u belešci [[Interpreter]]. Za bezbednost je bitno da se izrazi iz šablona izvršavaju tokom rada, a ne da li ih mehanizam tumači neposredno ili posle prevođenja.
- **Sandbox režim.** Neki mehanizmi imaju ograničen režim za šablone kojima se ne veruje. Jinja ga nudi za izvršavanje nepouzdanih šablona, ali u dokumentaciji navodi da sam sandbox nije rešenje za savršenu bezbednost. Odnosi se na [[Sandbox]] isto kao pojam: ograničava dozvoljene radnje, ali ne garantuje odsustvo ranjivosti.
- **Gde se izvršava.** Ova beleška opisuje mehanizme koji rade na serveru, u [[Procesna jedinica|procesnoj jedinici]] proizvoda. Postoje i mehanizmi koji šablone izračunavaju u pregledaču. Njihova zloupotreba je druga vrsta napada.
- Fakturis u osnovnoj studiji ne koristi mehanizam za šablone. Funkcija podsetnika i primer sa Jinja sintaksom su ilustrativni.
