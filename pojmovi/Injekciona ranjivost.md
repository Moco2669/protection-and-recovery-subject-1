---
tip: pojam
aliases: [injection vulnerability, injection flaw, ranjivost na injekciju]
izvor: 'MITRE CWE-74: https://cwe.mitre.org/data/definitions/74.html'
status: predlog
sloj: jezgro
---
# Injekciona ranjivost (injection vulnerability)

## Definicija
Injekciona ranjivost je ranjivost komponente koja od [[Nepouzdan ulaz|nepouzdanog ulaza]] sastavlja ceo ili deo upita, komande, dokumenta, šablona ili druge strukture podataka namenjene [[Parser|parseru]] ili [[Interpreter|interpreteru]], a ne sprečava da deo ulaza bude protumačen kao sintaksa umesto kao vrednost.

## Primer
U ilustrativnom izvozu e-faktura, [[Softverski proizvod|softverski proizvod]] [[Fakturis|Fakturisa]] sastavlja XML dokument spajanjem teksta: `"<napomena>" + napomena + "</napomena>"`. Napomenu upisuje korisnik. Ako napomena sadrži `</napomena>`, parser koji kasnije čita dokument videće kraj elementa tamo gde je programer očekivao samo tekst. Ranjivost postoji u tom delu koda čim je on objavljen, bez obzira na to da li ju je neko iskoristio. Pokušaj njenog iskorišćavanja opisan je u belešci [[Injekcioni napad]].

Kontraprimer: ako proizvod isti dokument gradi bibliotekom koja tekst napomene uvek zapisuje kao vrednost i znak `<` pretvara u `&lt;`, ista napomena ostaje tekst. Ranjivosti nema, iako je ulaz i dalje nepouzdan.

## Napomene
- **Tri uslova.** Ulaz je nepouzdan. Ulaz se ugrađuje u tekst ili strukturu koju zatim tumači neki parser ili interpreter. Između ta dva koraka nema mehanizma koji vrednost drži odvojenom od sintakse, kao što su [[Parametrizacija|parametrizacija]] ili [[Neutralizacija specijalnih elemenata|neutralizacija specijalnih elemenata]].
- **Nije uvek spajanje teksta.** CWE-74 govori o sastavljanju komande, strukture podataka ili zapisa. Kod [[NoSQL injekcija|NoSQL injekcije]] ulaz može da bude JSON objekat umesto očekivanog teksta, pa u upit uđe operator, a ne vrednost. Zato definicija govori o tumačenju dela ulaza kao sintakse, a ne o spajanju niski.
- **Mesto ranjivosti i mesto posledice ne moraju biti isti.** Ranjiva je komponenta koja sastavlja upit, komandu ili dokument. Kod XML izvoza posledica se ispoljava tek kada dokument pročita druga komponenta ili drugi sistem. Kod komande shell-a ili šablona, sastavljanje i tumačenje dešavaju se u istom procesu.
- **Vrste prema ciljnom jeziku.** MITRE ovu klasu vodi kao CWE-74, sa alternativnim nazivom „Injection“. Ispod nje su, između ostalih, XML injekcija (CWE-91), upiti nad podacima (CWE-943, kojoj pripadaju i XPath injekcija, CWE-643, i NoSQL injekcija), komande (CWE-77, sa OS komandama u CWE-78) i generisanje koda (CWE-94, sa šablonima u CWE-1336). Odgovarajući napadi opisani su u belešci [[Injekcioni napad]].
- **Klasifikacija XXE ranjivosti u CWE hijerarhiji.** CWE-611 nalazi se ispod CWE-610 (Externally Controlled Reference to a Resource in Another Sphere), a ne ispod CWE-74. Tamo napadač ne izlazi iz vrednosti u sintaksu, nego šalje ceo dokument, a ranjivost je u podešavanju parsera. Videti [[Napad spoljnim XML entitetom]].
- **Nastanak i posledice.** Injekciona ranjivost najčešće nastaje u implementaciji, kada se ulaz ugrađuje bez razdvajanja vrednosti od sintakse. Prava [[Servisni nalog|servisnog naloga]] i ograničenja [[Sistemsko okruženje|sistemskog okruženja]] ne određuju da li ranjivost postoji. Ona određuju koliku štetu može da napravi uspešan napad.
