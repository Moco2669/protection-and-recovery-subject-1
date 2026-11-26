---
tip: pojam
aliases: [XML external entity attack, XXE, XXE napad, XML External Entity injection]
izvor: 'MITRE CWE-611: https://cwe.mitre.org/data/definitions/611.html; OWASP XML External Entity Prevention Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/XML_External_Entity_Prevention_Cheat_Sheet.html; PortSwigger Web Security Academy, XXE injection: https://portswigger.net/web-security/xxe; Python dokumentacija, XML security: https://docs.python.org/3/library/xml.html'
status: predlog
sloj: jezgro
---
# Napad spoljnim XML entitetom (XML external entity attack)

## Definicija
Napad spoljnim XML entitetom je napad u kome napadač komponenti dostavlja XML dokument koji deklariše spoljni [[XML entitet]], kako bi [[Parser|parser]] te komponente pri obradi razrešio entitet i pristupio resursu na koji on upućuje.

## Primer
U ilustrativnoj funkciji uvoza e-faktura, korisnik [[Fakturis|Fakturisa]] otprema XML fakturu, a [[Softverski proizvod|proizvod]] je parsira na aplikacionom [[Server|serveru]] i prikazuje uvezenu napomenu. Napadač, prijavljen kao korisnik, otprema dokument čiji interni podskup deklariše spoljni entitet sa adresom datoteke na serveru, a u elementu `napomena` koristi referencu na taj entitet. Ako parser razrešava spoljne entitete, na mesto reference stavlja sadržaj te datoteke, na primer podešavanja proizvoda, a proizvod ga prikaže napadaču kao napomenu. Ishod je [[Narušavanje poverljivosti podataka|narušavanje poverljivosti]]. Scenario je ilustracija: studija ne određuje ni operativni sistem ni XML biblioteku Fakturisa.

Kontraprimer: ako je parser podešen da odbija dokumente sa deklaracijom tipa dokumenta, isti dokument se odbija pre obrade i nijedna datoteka se ne čita. Pokušaj napada je i tada postojao, ali nije uspeo. Ni [[XML injekcija]] nije ovaj napad. Tamo napadač kontroliše samo vrednost jednog polja u dokumentu koji piše proizvod, a ovde ceo dokument koji proizvod čita.

## Napomene
- **Gde je ranjivost.** U podešavanju parsera koji obrađuje dokumente iz nepouzdanog izvora i pri tome razrešava spoljne entitete. Dokument napadača je ispravan XML. On koristi funkciju jezika koju parser nije trebalo da dozvoli.
- **Kada parser zaista učita resurs.** Da bi napad iz primera uspeo, moraju da važe svi uslovi: parser prihvata deklaraciju tipa dokumenta, razrešava spoljne opšte entitete, podržava šemu adrese (na primer `file:` ili `http:`) i proces parsera ima pravo da pročita datoteku ili otvori vezu. Specifikacija ne obavezuje parser koji ne proverava validnost da učitava spoljne entitete ni spoljni podskup, pa ishod zavisi od biblioteke i njenog podešavanja. Pojmovi DTD, podskup i vrste entiteta objašnjeni su u belešci [[XML entitet]]. Da bi napadač video sadržaj, proizvod mora i da prikaže vrednost u kojoj je referenca stajala. Ako to ne radi, napad je slep.
- **Kada sadržaj nije prihvatljiv kao XML.** Sadržaj spoljnog entiteta parsira se kao deo dokumenta, pa mora biti dobro formiran XML sadržaj. Datoteka u kojoj se pojavljuju `<` ili `&` koji ne čine ispravne oznake ili reference dovodi do greške pri parsiranju, a ne do prikaza sadržaja. Ako aplikacija korisniku prikazuje poruke parsera, i sama greška može da otkrije deo sadržaja datoteke.
- **Naziv i klasifikacija.** XXE se često naziva „XXE injection“. MITRE ranjivost koja ga omogućava klasifikuje kao CWE-611, ispod CWE-610 (Externally Controlled Reference to a Resource in Another Sphere), odvojeno od CWE-74, a OWASP Top 10:2021 CWE-611 mapira u kategoriju A05 Security Misconfiguration. U ovoj bazi XXE se obrađuje zasebno od [[XML injekcija|XML injekcije]] i ostalih vrsta [[Injekcioni napad|injekcionog napada]], jer napadač koristi deklaraciju spoljnog entiteta i nesigurno razrešavanje resursa, umesto da ubacivanjem oznaka u polje promeni strukturu XML dokumenta. Zato ga [[Neutralizacija specijalnih elemenata|neutralizacija]] vrednosti ne sprečava.
- **Posledice prema CWE-611.** Čitanje lokalnih datoteka, slanje odlaznih zahteva sa servera ka adresama koje odredi napadač, uključujući interne servise (SSRF, CWE-918), i trošenje procesora i memorije kada entitet upućuje na veliki resurs ([[Narušavanje dostupnosti resursa]]).
- **Slepa varijanta.** Kada aplikacija ne vraća vrednosti spoljnih entiteta u odgovoru, PortSwigger opisuje dva pristupa. U prvom, napadač parser navodi na mrežnu interakciju sa sistemom koji kontroliše, koristeći [[XML entitet|parametarske entitete]] i zlonamerni spoljni DTD koji drži na svom serveru. U drugom, izaziva grešku pri parsiranju čija poruka sadrži traženi podatak.
- **Skriveni XML.** Isti napad moguć je kroz formate koji u sebi sadrže XML. Takvi su dokumenti formata DOCX i XLSX, slike SVG i SOAP i SAML poruke. Program koji obrađuje takvu datoteku koristi XML parser, iako korisniku izgleda da učitava dokument ili sliku.
- **Tri napada na XML, razgraničenje.** Kod [[XML injekcija|XML injekcije]] napadač kontroliše vrednost u dokumentu koji piše komponenta. Kod napada spoljnim XML entitetom kontroliše ceo dokument, a parser pristupa spoljnom resursu. Kod proširivanja entiteta („billion laughs“), opisanog u belešci [[XML entitet]], takođe kontroliše ceo dokument, ali koristi samo unutrašnje entitete i ugrožava dostupnost.
- **Zaštita.** Bezbedno podešavanje parsera je [[Tehnička kontrola|tehnička]] i [[Preventivna kontrola|preventivna kontrola]]. Prema OWASP-u:
  - DTD treba isključiti kad god je to moguće, a deklaracije tipa dokumenta odbiti, ako parser to podržava. To sprečava i ovaj napad i proširivanje entiteta.
  - Ako je DTD neophodan, isključuju se razrešavanje spoljnih entiteta i učitavanje spoljnog DTD-a, a proširivanje entiteta se ograničava.
  - XInclude (W3C mehanizam za uključivanje drugih XML dokumenata) treba da ostane isključen ako nije potreban, jer može da učita resurse nezavisno od DTD-a.
  - Primer za Javu, iz OWASP preporuka:

    ```java
    DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();
    dbf.setFeature("http://apache.org/xml/features/disallow-doctype-decl", true);
    ```

    Parser tada odbija svaki dokument sa deklaracijom tipa dokumenta, pa i dokument iz primera. Ispravne e-fakture bez DTD-a uvoze se kao i ranije. Izbor Jave je ilustrativan.
- **Podrazumevana ponašanja se razlikuju.** OWASP navodi da su neki .NET parseri zaštićeni tek od verzije 4.5.2. Python dokumentacija navodi da Expat podrazumevano ne pristupa lokalnim datotekama niti otvara mrežne veze. Zato se podešavanje utvrđuje za svaku biblioteku i verziju, i za svako mesto u kodu na kome se XML parsira, uključujući i biblioteke koje čitaju DOCX, XLSX ili SVG.
- **XSD provera nije zamena.** Provera prema XSD šemi utvrđuje oblik dokumenta u kome su reference na entitete već zamenjene sadržajem, pa ne sprečava učitavanje spoljnog resursa. OWASP upozorava i da obrada i provera šeme mogu same da učitaju spoljne resurse.
- **Ograničenje štete.** Prava [[Servisni nalog|servisnog naloga]] pod kojim radi parser određuju koje datoteke on uopšte može da pročita i do kojih mrežnih adresa može da stigne. To ne zamenjuje podešavanje parsera.
