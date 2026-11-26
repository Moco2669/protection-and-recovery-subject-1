---
tip: pojam
aliases: [neutralization of special elements, escaping, output encoding, kodiranje izlaza]
izvor: 'MITRE CWE-116: https://cwe.mitre.org/data/definitions/116.html; OWASP Injection Prevention Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Injection_Prevention_Cheat_Sheet.html; Python dokumentacija, shlex: https://docs.python.org/3/library/shlex.html'
status: predlog
sloj: jezgro
---
# Neutralizacija specijalnih elemenata (neutralization of special elements)

## Definicija
Neutralizacija specijalnih elemenata je [[Tehnička kontrola|tehnička]] i [[Preventivna kontrola|preventivna kontrola]] u kojoj komponenta, pre nego što vrednost ugradi u izraz, upit, komandu ili dokument, znakove i nizove znakova koji na tom mestu u jeziku odredišta imaju posebno značenje zapisuje u obliku koji [[Parser|parser]] tog jezika čita kao deo vrednosti, a ne kao sintaksu.

## Primer
Pri ilustrativnom izvozu e-fakture, [[Softverski proizvod|proizvod]] [[Fakturis|Fakturisa]] napomenu `Cena < 1000 & popust` zapisuje kao `Cena &lt; 1000 &amp; popust`. XML parser pri uvozu vraća prvobitni tekst, pa kupac vidi istu napomenu koju je korisnik upisao. Na isti način napomena iz primera beleške [[XML injekcija]] ne može da zatvori element `napomena` ni da doda novi `izdavalac`, jer njen `<` postaje `&lt;`.

Kontraprimer: ako proizvod isti tekst neutralizuje pravilima XML-a, a zatim ga ugradi u komandu shell-a, znak `;` ostaje nepromenjen. Neutralizacija za pogrešan jezik ne štiti.

## Napomene
- **Šta radi, a šta ne.** Neutralizacija ne odbija vrednost i ne menja njeno značenje: parser na odredištu vraća prvobitni tekst. Po tome se razlikuje od [[Validacija ulaza|validacije ulaza]], koja ulaz koji ne odgovara pravilima odbija, i od sanitizacije ili filtriranja, koje znakove uklanja. Od [[Parametrizacija|parametrizacije]] se razlikuje po tome što vrednost i struktura ostaju u istom tekstu, a bezbednost zavisi od toga da li su pravila za taj jezik i to mesto primenjena potpuno.
- **Pravila zavise od jezika i mesta u njemu.** CWE-116 traži da se razume kontekst u kome će podatak biti upotrebljen i kodiranje koje se tamo očekuje, a OWASP da se koristi sintaksa escaping-a tog interpretera. Isti jezik može imati različita pravila na različitim mestima.
  - **XML.** U tekstu elementa posebno značenje imaju `<`, `&` i niz `]]>`. U vrednosti atributa to su `<`, `&` i navodnik kojim je vrednost omeđena. Zapisi `&lt;`, `&amp;`, `&gt;`, `&quot;` i `&apos;` navedeni su u belešci [[XML injekcija]]. XML biblioteke koje grade dokument primenjuju ova pravila same, pri zapisivanju dokumenta u tekst (videti napomenu o XML-u u belešci [[Parametrizacija]]).
  - **XPath.** U XPath 1.0 literal ne može da sadrži navodnik kojim je otvoren, a gramatika nema escaping. Vrednost sa oba navodnika mora se sastaviti funkcijom `concat()`, kako je opisano u belešci [[XPath]]. XPath 3.1 dozvoljava da se navodnik u literalu zapiše dvaput, `''` ili `""`. Ispravna pravila zato zavise i od verzije jezika koju biblioteka primenjuje. Kada interfejs podržava XPath promenljive, prednost ima parametrizacija, a MITRE za XPath kao meru navodi parametrizovane upite.
  - **Shell.** Pravila zavise od shell-a i operativnog sistema. Python funkcija `shlex.quote()` vraća vrednost zapisanu tako da se u komandnoj liniji može upotrebiti kao jedna reč, ali dokumentacija upozorava da je namenjena samo Unix shell-ovima i da nije garantovano ispravna na shell-ovima koji ne prate POSIX, na primer na Windows-u. OWASP navodi escaping prema operativnom sistemu kao jednu od mogućnosti, uz ograničenje: posle escaping-a napadač i dalje može da preda jedan argument, pa ubacivanje argumenata ostaje moguće. MITRE neutralizaciju smatra delotvornijom od same validacije, ali kao prve mere navodi pozive biblioteke i strukturisane mehanizme. Zato je neutralizacija rezervno rešenje kada se shell ne može izbeći, a ne zamena za pokretanje programa bez shell-a ([[Injekcija OS komandi]]).
- **Gde neutralizacija ne pomaže.**
  - **Injekcija šablona.** Jezik šablona ima mnogo konstrukcija, i one se razlikuju između mehanizama. OWASP savetuje da se sintaksa šablona ne pokušava filtrirati iz ulaza. Kodiranje izlaza u samom šablonu, na primer kodiranje za HTML, primenjuje se na vrednosti koje šablon ispisuje, pa prema OWASP-u ne sprečava SSTI. To je isti problem kao u kontraprimeru: pravila jednog jezika primenjena su na drugi. Kada korisnik sme da uređuje samo zatvoren skup oznaka, zaštita je provera prema listi dozvoljenih oznaka ili zamena koju proizvod radi sam, opisane u belešci [[Serverska injekcija šablona]].
  - **NoSQL injekcija u MongoDB-u.** Upit je objekat, a ne tekst, pa nema znakova koje bi trebalo zapisati drugačije. Problem je tip vrednosti, objekat umesto teksta, i rešava se izričitim `$eq` i proverom tipa ([[NoSQL injekcija]]).
  - **Napad spoljnim XML entitetom.** Napadač ne ubacuje vrednost u dokument koji piše proizvod, nego dostavlja ceo dokument. Zaštita je podešavanje parsera, opisano u belešci [[Napad spoljnim XML entitetom]].
- **Kada se koristi.** OWASP je navodi kao rešenje kada parametrizovan interfejs nije dostupan, a za XML dokument ona je uobičajena mera, jer je tekst dokumenta krajnji oblik u kome se vrednost prenosi.
- **Gotove funkcije i mesto primene.** Neutralizuje se funkcijom biblioteke namenjene tom jeziku, a ne ručno, jer ručna pravila lako propuste neki znak ili kontekst. Neutralizuje se na mestu gde se vrednost ugrađuje u drugi jezik, a ne na mestu gde ulazi u sistem, jer se tek tamo zna jezik odredišta. CWE-116 može da prethodi injekciji (CWE-74), a validaciju preporučuje kao dopunsku meru koja smanjuje posledice grešaka u kodiranju.
