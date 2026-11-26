---
tip: pojam
aliases: [injection attack, injection, napad ubacivanjem]
izvor: 'definicija napada sa predavanja ZOSS 03; MITRE CWE-74: https://cwe.mitre.org/data/definitions/74.html; OWASP Injection Prevention Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Injection_Prevention_Cheat_Sheet.html'
status: predlog
sloj: jezgro
---
# Injekcioni napad (injection attack)

## Definicija
Injekcioni napad je napad u kome napadač pripremljenim [[Nepouzdan ulaz|ulazom]] pokušava da iskoristi [[Injekciona ranjivost|injekcionu ranjivost]], tako da deo tog ulaza bude protumačen kao sintaksa i promeni značenje upita, komande, dokumenta ili šablona koji komponenta sastavlja.

## Primer
U ilustrativnom izvozu e-faktura iz beleške [[Injekciona ranjivost]], [[Softverski proizvod|proizvod]] [[Fakturis|Fakturisa]] napomenu ugrađuje u XML dokument spajanjem teksta. Napadač, registrovan kao korisnik, u napomenu upisuje tekst koji počinje sa `x</napomena>` i nastavlja se novim elementom `<izdavalac>` sa tuđim PIB-om. Time pokušava da u izvezenu fakturu doda podatke koje proizvod inače upisuje sam. Ako je izvoz ranjiv, dokument dobija dodatni element, a posledica se vidi kod primaoca koji fakturu uveze. Ako izvoz neutralizuje napomenu, pokušaj ne uspeva, ali je i dalje injekcioni napad, jer je napadač pokušao da iskoristi ranjivost. Detalji su u belešci [[XML injekcija]].

Kontraprimer: korisnik koji u napomenu upiše „Cena < 1000 & popust“ ne izvodi injekcioni napad, iako tekst sadrži znakove koji su u XML-u posebni. On ne pokušava da promeni strukturu dokumenta. Ako je izvoz ranjiv, njegova napomena može da pokvari dokument, ali to je greška u obradi, a ne napad.

## Napomene
- **Vrste u ovoj bazi**, prema jeziku koji tumači ubačeni deo:
  - struktura XML dokumenta: [[XML injekcija]]
  - jezici upita nad podacima: [[XPath injekcija]], [[NoSQL injekcija]]
  - komande i izvršavanje koda: [[Injekcija OS komandi]], [[Serverska injekcija šablona]]
- **Ulaz ne mora biti tekst.** Pripremljen ulaz može biti i struktura podataka. Kod [[NoSQL injekcija|NoSQL injekcije]] to je JSON objekat sa operatorom upita na mestu gde komponenta očekuje tekst.
- **Ishodi** zavise od toga šta ciljni jezik i interpreter omogućavaju i od prava procesa koji ga izvršava: čitanje tuđih podataka ([[Narušavanje poverljivosti podataka]]), izmena podataka ([[Narušavanje integriteta podataka]]), predstavljanje u ime drugog ([[Lažno predstavljanje]]), iscrpljivanje resursa ([[Narušavanje dostupnosti resursa]]) i izvršavanje radnji sa pravima [[Servisni nalog|servisnog naloga]] procesa ([[Dobijanje prevelikih privilegija]]).
- **Pripremljen ulaz** je [[Nepouzdan ulaz|nepouzdan ulaz]] koji napadač namerno sastavlja tako da iskoristi [[Injekciona ranjivost|injekcionu ranjivost]]. Najčešće je to kratak tekst ili objekat u polju forme, parametru ili telu [[HTTP]] zahteva.
- **Slepa injekcija.** Kada odgovor ne prikazuje rezultat ubačenog dela, napadač zaključuje posredno: postavlja uslove na koje dobija drugačiji odgovor, izaziva kašnjenje ili navodi sistem da pošalje zahtev na adresu koju napadač prati.
- **Injekcija drugog reda.** Ulaz se najpre bezbedno sačuva, a kasnije ga druga funkcija pročita i ugradi u upit ili komandu. Napad se dešava u drugom koraku, pa ga provera na ulazu prvog koraka ne otkriva.
- **Program se izvršava kako je napisan.** Kod injekcionog napada memorija procesa nije narušena. Napadač ubacuje deo ulaza u jezik višeg nivoa (XML, XPath, upit baze, komandu shell-a, šablon), koji program namerno predaje parseru ili interpreteru.
- **Srodan napad na parser.** [[Napad spoljnim XML entitetom]] se u praksi naziva „XXE injection“, ali se njegov mehanizam razlikuje od vrsta opisanih u ovoj belešci. Napadač ne ubacuje sintaksu u vrednost koju komponenta ugrađuje u dokument, upit ili komandu, nego koristi deklaraciju spoljnog XML entiteta i nesigurno razrešavanje resursa u parseru. Klasifikacija je objašnjena u njegovoj belešci.
- MITRE CAPEC opisuje istu ideju za komande: napadač ubacuje nove elemente u postojeću komandu i time menja njeno tumačenje (CAPEC-248).
- OWASP navodi i vrste koje ova grana ne obrađuje, na primer injekcije u LDAP upite, ORM, Expression Language i OGNL.
