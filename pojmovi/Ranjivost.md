---
tip: pojam
aliases: [vulnerability]
izvor: NIST SP 800-30 Rev. 1, Appendix B Glossary, "vulnerability"; ISO/IEC 27000:2018, 3.77 vulnerability
status: predavanje
sloj: temelj
---
# Ranjivost (vulnerability)

## Definicija
Ranjivost je osobina [[Komponenta sistema|komponente sistema]] zbog koje komponenta omogućava radnju suprotnu nekom [[Bezbednosni zahtev|bezbednosnom zahtevu]], a kojom [[Napadač|napadač]] može da ostvari [[Pretnja|pretnju]].

## Primer
Zahtev u aplikaciji [[Fakturis]] glasi: fakturu vide samo korisnik koji ju je izdao i kupac kome je upućena. Adresa `/api/fakture/{id}` vraća fakturu svakom prijavljenom korisniku koji zna njen broj, a brojevi faktura idu redom. Svaki registrovani korisnik tako može da pročita tuđe fakture. To je ranjivost web aplikacije.

Kontraprimeri: javna stranica sa cenovnikom dostupna je svima, i to je u skladu sa zahtevima. Stari modul za uvoz kupaca iz XML fajla ima grešku u obradi XML-a, ali je isključen i do njega ne vodi nijedan zahtev. Nijedno od ova dva ne omogućava nedozvoljenu radnju, pa nisu ranjivosti.

## Napomene
- Ranjivost nastaje u dizajnu, implementaciji, konfiguraciji ili načinu upotrebe komponente. U Fakturisu: izostanak provere vlasništva fakture je greška dizajna i implementacije, fabrička lozinka rutera greška konfiguracije, a otvaranje priloga bez provere pošiljaoca greška upotrebe.
- Nedostatak iz kontraprimera sa XML modulom je [[Slabost|slabost]]: ako se modul ponovo uključi, postaće ranjivost.
- Pregled poznatih ranjivosti Fakturisa nalazi se u beleški konteksta, odeljak *Poznate ranjivosti*. Ranjivosti opisane u bazi, po komponenti na kojoj se najčešće javljaju:
  - [[Zaposleni]]: [[Podložnost socijalnom inženjeringu]]
  - [[Poslovni računar]] i [[Mrežni prolaz]]: [[Pogrešna bezbednosna konfiguracija]]
  - [[Interna mreža]]: [[Nedostatak segmentacije mreže]]
  - [[Server]]: [[Nezakrpljen softver]]
  - [[Web aplikacija]]: [[Neispravna kontrola pristupa]], [[Injekcija]], [[Nedovoljna provera autentičnosti podataka]], [[Nekontrolisana učestalost zahteva]]
  - [[Baza podataka]] i [[Skladište dokumenata]]: [[Prekomerno ovlašćenje]]
  - [[Repozitorijum izvornog koda]]: [[Ugrađeni pristupni podatak]]
  - [[Sistem za upravljanje nalozima]]: [[Slaba autentifikacija]]
  - [[Sistem za zapise o radu]]: [[Nedovoljno beleženje i praćenje]]
  - [[Sistem za rezervne kopije]]: [[Nezaštićena rezervna kopija]]
