---
tip: pojam
aliases: [untrusted input, untrusted data, nepouzdani podaci]
izvor: 'nema posebne standardne definicije; srodno: MITRE CWE-74: https://cwe.mitre.org/data/definitions/74.html; OWASP Injection Prevention Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Injection_Prevention_Cheat_Sheet.html'
status: predlog
sloj: temelj
---
# Nepouzdan ulaz (untrusted input)

## Definicija
Nepouzdan ulaz je podatak koji komponenta prima iz izvora na čiji sadržaj napadač može da utiče, pa komponenta ne sme da pretpostavi da on ima oblik, dužinu ili značenje koje očekuje.

## Primer
Kada korisnik [[Fakturis|Fakturisa]] u formu fakture upiše napomenu, [[Softverski proizvod|softverski proizvod]] prima nepouzdan ulaz. Korisnikom i njegovim uređajem ne upravlja firma, pa napomena može da sadrži bilo koji niz znakova, a ne samo rečenicu poput „Rok plaćanja 15 dana“. Isto važi za XML e-fakturu koju korisnik uveze, iako ju je pripremio njegov dobavljač, i za broj fakture i kontrolni kod koje kupac pošalje pri pregledu fakture.

Kontraprimer: fiksni tekst podsetnika koji su programeri Fakturisa napisali u izvornom kodu i objavili iz [[Repozitorijum izvornog koda|repozitorijuma]] nije nepouzdan ulaz u ovom smislu, pod pretpostavkom da su repozitorijum i proces objavljivanja zaštićeni, pa je integritet koda očuvan. Ako napadač ipak može da izmeni kod, to je [[Narušavanje integriteta podataka|narušavanje integriteta]] koda, a ne problem obrade ulaza. Tekst podsetnika koji korisnik sam prilagodi, kao u belešci [[Serverska injekcija šablona]], jeste nepouzdan ulaz.

## Napomene
- Pouzdanost se određuje prema izvoru podatka, a ne prema njegovom sadržaju. Napomena koja izgleda bezazleno i dalje je nepouzdan ulaz.
- Mesta na kojima nepouzdan ulaz ulazi u sistem pronalaze se na [[Dijagram toka podataka|dijagramu toka podataka]]: to su [[Tok podataka|tokovi]] koji od [[Spoljni entitet|spoljnog entiteta]] prelaze [[Granica poverenja|granicu poverenja]]. Granica nije jedini izvor. Podatak koji je korisnik ranije upisao, pa ga proizvod kasnije pročita iz [[Baza podataka|baze]], ostaje nepouzdan. Na tome se zasniva injekcija drugog reda, opisana u belešci [[Injekcioni napad]].
- Nepouzdan ulaz nije isto što i zlonameran. Većina takvih podataka je ispravna. Komponenta samo ne sme da zavisi od toga.
- Provera ulaza ne čini podatak pouzdanim za svaku dalju upotrebu. Naziv koji je prošao [[Validacija ulaza|validaciju ulaza]] za prikaz na ekranu može i dalje da sadrži znakove koji su posebni u nekom drugom jeziku. Zato se bezbednost proverava na mestu gde se podatak ugrađuje u upit, komandu ili dokument.
- CWE za istu ideju koristi izraz „externally-influenced input“, a OWASP „untrusted data“.
