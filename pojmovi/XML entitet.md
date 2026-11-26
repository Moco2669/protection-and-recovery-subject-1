---
tip: pojam
aliases: [XML entity]
izvor: 'W3C, XML 1.0 (Fifth Edition): https://www.w3.org/TR/xml/; OWASP XML External Entity Prevention Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/XML_External_Entity_Prevention_Cheat_Sheet.html; Python dokumentacija, XML security: https://docs.python.org/3/library/xml.html'
status: predlog
sloj: temelj
---
# XML entitet (XML entity)

## Definicija
XML entitet je imenovana jedinica sadržaja koju XML dokument deklariše i na koju se poziva referencom, a [[Parser|parser]] pri obradi dokumenta na mesto reference stavlja sadržaj entiteta. Sadržaj unutrašnjeg entiteta zapisan je u njegovoj deklaraciji, dok se sadržaj spoljnog entiteta nalazi u spoljašnjem resursu koji parser može da učita, u zavisnosti od svog ponašanja i podešavanja.

## Primer
Dobavljač korisnika [[Fakturis|Fakturisa]] mogao bi da pošalje e-fakturu u kojoj je naziv firme deklarisan jednom i korišćen na više mesta:

```xml
<!DOCTYPE faktura [
  <!ENTITY firma "Mesara Zlatibor d.o.o.">
]>
<faktura>
  <napomena>Isporuku vrši &firma;</napomena>
</faktura>
```

Posle obrade, proizvod u elementu `napomena` vidi tekst „Isporuku vrši Mesara Zlatibor d.o.o.“. Ovo je unutrašnji entitet, deklarisan u internom podskupu. Kada bi deklaracija glasila `<!ENTITY firma SYSTEM "file:///…">`, to bi bio spoljni entitet, i parser bi, ako razrešava spoljne entitete, njegov sadržaj pročitao iz datoteke na računaru na kome radi.

Kontraprimer: `&#60;` nije referenca na entitet nego referenca na znak. Ona označava znak `<` preko njegovog broja i ne zahteva nikakvu deklaraciju.

## Napomene
- **DOCTYPE i DTD.** Deklaracija tipa dokumenta počinje sa `<!DOCTYPE`, stoji pre korenog elementa i sadrži ili upućuje na deklaracije elemenata, atributa i entiteta. Te deklaracije zajedno čine DTD (document type definition). Deklaracije zapisane u uglastim zagradama u samom dokumentu, kao u primeru, čine interni podskup. Deklaracije u datoteci na koju `DOCTYPE` upućuje čine spoljni podskup. Dokument može imati oba.
- **Dve različite podele.** Interni i spoljni podskup govore o tome gde stoje deklaracije. Unutrašnji i spoljni entitet govore o tome odakle dolazi sadržaj entiteta. Spoljni entitet može biti deklarisan u internom podskupu, a tako izgleda i dokument u [[Napad spoljnim XML entitetom|napadu spoljnim XML entitetom]]. Spoljni podskup je takođe resurs na adresi: parser koji ga učita pristupa toj adresi i kada dokument nema nijedan spoljni entitet.
- **Šta parser mora da obradi.** Specifikacija parser koji ne proverava validnost obavezuje da obradi deklaracije iz internog podskupa, sve do prve reference na parametarski entitet koji ne učitava. Zato unutrašnji entiteti iz primera rade i bez provere validnosti. Spoljni podskup i spoljne entitete takav parser ne mora da učita. Da li ih učitava zavisi od biblioteke, verzije i podešavanja, pa se to ne pretpostavlja, nego utvrđuje.
- **SYSTEM i PUBLIC.** Spoljni entitet i spoljni podskup zadaju se spoljnim identifikatorom oblika `SYSTEM "adresa"` ili `PUBLIC "javni identifikator" "adresa"`. Adresa je URI referenca, na primer putanja do lokalne datoteke ili mrežna adresa. Prema gramatici specifikacije, i oblik `PUBLIC` mora da sadrži adresu, pa i takva deklaracija upućuje na resurs koji parser može da učita. Koje šeme URI-ja parser prihvata zavisi od biblioteke.
- **Opšti i parametarski entiteti.** Opšti entitet koristi se u sadržaju dokumenta referencom `&ime;`. Parametarski entitet, označen sa `%` i korišćen referencom `%ime;`, sme da se koristi samo unutar DTD-a. Pet opštih entiteta je unapred definisano i parser ih uvek prepoznaje: `&lt;`, `&gt;`, `&amp;`, `&apos;` i `&quot;`.
- **Proširivanje entiteta („billion laughs“, XML bomba).** Unutrašnji entitet može da sadrži reference na druge entitete. U klasičnom obliku osnovni entitet sadrži kratak tekst, npr. „lol“, a svaki od sledećih devet entiteta sadrži po deset referenci na prethodni. Poslednji entitet se tako proširuje u 10⁹ ponavljanja osnovnog teksta, oko tri gigabajta, iako dokument ima manje od jednog kilobajta. Napad iscrpljuje memoriju i procesor parsera i vodi ka [[Narušavanje dostupnosti resursa|narušavanju dostupnosti]]. MITRE ga vodi kao CWE-776, sa alternativnim nazivima „Billion Laughs Attack“, „XML Bomb“ i „XEE“. Srodna varijanta („quadratic blowup“) mnogo puta ponavlja jedan veliki entitet, bez ugnježdavanja.
- **Zaštita od proširivanja nije isto što i zaštita od spoljnih entiteta.** Proširivanje koristi samo unutrašnje entitete i ne pristupa nijednom spoljnom resursu. Zato isključivanje razrešavanja spoljnih entiteta, koje štiti od napada spoljnim XML entitetom, ne zaustavlja ovaj napad. OWASP to kaže izričito: resolver ne ograničava proširivanje unutrašnjih entiteta. Od oba napada štiti odbijanje deklaracije tipa dokumenta. Ako DTD mora da ostane, potrebno je i ograničenje broja i veličine proširenih entiteta. Python dokumentacija, na primer, navodi da su verzije parsera Expat starije od 2.7.2 podložne ovom napadu.
- Spoljni XML entitet nema veze sa pojmom [[Spoljni entitet]] sa dijagrama toka podataka. Ovde je reč o delu XML dokumenta, a tamo o osobi ili sistemu izvan modelovanog sistema.
