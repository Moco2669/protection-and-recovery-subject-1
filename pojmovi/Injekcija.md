---
tip: pojam
aliases: ["injection"]
izvor: "OWASP Top 10:2025 — A05 Injection, https://top10.owasp.org/2025/A05_2025-Injection/; MITRE CWE-74, https://cwe.mitre.org/data/definitions/74.html"
---

# Injekcija (injection)

## Definicija

Injekcija jeste [[Slabost|slabost]] u obradi podataka zbog koje komponenta sistema ne razdvaja pouzdano ulazne podatke od naredbi ili upita, pa ulaz pod kontrolom napadača može da promeni njihovo značenje ili izvršavanje.

## Primer

U posmatranom sistemu firme, korisnik u polje za pretragu unosi ime kupca. Aplikacija od tog teksta sastavlja upit kojim od baze traži: „Pronađi ovog kupca među kupcima mog preduzeća.“

Aplikacija, međutim, ne odvaja uneseni tekst od naredbe za bazu. Napadač zato može uneti tekst koji promeni značenje upita u: „Prikaži sve kupce, bez obzira na preduzeće.“

Baza izvrši izmenjeni upit i vrati i tuđe kupce. Slabost je u tome što aplikacija dozvoljava da tekst za pretragu postane deo naredbe, umesto da ostane samo podatak koji se traži.

## Napomene

SQL injekcija je jedna vrsta injekcije. Sličan problem može nastati pri sastavljanju naredbi operativnog sistema ili sadržaja koji pregledač tumači kao izvršivi kod.

Ulaz ne mora dolaziti iz vidljivog polja obrasca. Može stići kroz API zahtev, poruku spoljnog servisa ili prethodno sačuvane podatke.

Sama upotreba posebnih znakova u unosu nije napad. Problem nastaje kada način obrade omogućava da se podaci protumače kao deo naredbe ili upita.
