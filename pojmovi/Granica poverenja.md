---
tip: pojam
aliases: [trust boundary, security boundary]
izvor: Microsoft SDL, Secure by Design, "A trust boundary is a logical construct" ([web](https://www.microsoft.com/en-us/securityengineering/sdl/practices/secure-by-design)); Shostack, Experiences Threat Modeling at Microsoft, 2008, odeljak 3.1 ([PDF](https://shostack.org/files/papers/modsec08/Shostack-ModSec08-Experiences-Threat-Modeling-At-Microsoft.pdf))
status: predlog
sloj: jezgro
---
# Granica poverenja (trust boundary)

## Definicija
Granica poverenja je logička linija koja na modelu razdvaja delove sistema sa različitim pretpostavkama o tome ko njima upravlja i koliko su pouzdani.

## Primer
Na [[Dijagram toka podataka|dijagramu toka podataka]] firme [[Fakturis]], isprekidana granica može da obuhvati softverski proizvod, bazu i skladište datoteka kojima upravlja firma. Korisnik i [[Spoljni servis|spoljni servis za naplatu]] ostaju izvan nje. Tok korisnikovih stavki ka proizvodu i poziv proizvoda ka servisu prelaze granicu.

Kontraprimer: svaka linija između dve komponente nije granica poverenja. Ako obe komponente imaju iste pretpostavke poverenja i pod istom kontrolom su, sama njihova povezanost ne stvara takvu granicu.

## Napomene
- Granica poverenja je logička, ne mora da se poklapa sa zidom, ruterom ili fizičkom granicom mreže.
- [[Tok podataka|Tokovi podataka]] koji prelaze granicu zahtevaju posebnu proveru: da li treba autentifikovati učesnika, proveriti pravo pristupa, validirati podatke ili zaštititi komunikaciju.
- Granica sama ne obezbeđuje zaštitu; ona označava mesto na kojem se bezbednosne pretpostavke menjaju.
- Na dijagramu se često prikazuje isprekidanom linijom ili okvirom.

## Kako odrediti gde je postaviti
1. Odredi opseg sistema i na [[Dijagram toka podataka|dijagramu toka podataka]] prikaži njegove glavne elemente i tokove.
2. Za svaki element ili učesnika utvrdi ko njime upravlja, ko može da mu pristupi i koja pravila i kontrole važe.
3. Grupiši elemente za koje važe slične pretpostavke. Granicu postavi između grupa kada se pretpostavke o kontroli, privilegijama ili pravilima pristupa bitno razlikuju.
4. Označi [[Tok podataka|tokove]] koji prelaze granicu i razmotri da li treba proveriti identitet, pravo pristupa i validnost podataka ili zaštititi prenos.

Granica se određuje dok se pravi početni model, kada su elementi i tokovi već ucrtani, a pre sistematske analize pretnji. Preispituje se kada se promene opseg sistema, upravljanje komponentama, prava pristupa ili kontrole.

## Primeri postavljanja
U ovim primerima, **zona** je grupa elemenata za koje važe slična pravila pristupa i kontrole. Broj uređaja sam po sebi ne određuje broj zona.

- **Korisnik i Fakturis:** u modelu koji obuhvata komponente pod kontrolom firme, korisnik je izvan granice, a [[Softverski proizvod|proizvod]] unutar nje. Tok stavki fakture prelazi granicu.
- **Aplikacioni server i PostgreSQL u istoj zoni:** u postojećoj skici [[Fakturis]] PostgreSQL je na aplikacionom serveru. Ako model ne prikazuje posebnu podelu pristupa ili kontrole između njih, mogu se prikazati u istoj zoni. Tok aplikacije ka bazi ne prelazi unutrašnju granicu.
- **Aplikacioni server i PostgreSQL u različitim zonama:** hipotetički, baza je izdvojena u zaštićenu mrežnu zonu. Zaštitni zid dozvoljava pristup PostgreSQL-u samo sa aplikacionog servera, a aplikacija koristi nalog sa ograničenim pravima. Tada se granica crta između aplikacionog servera i baze, a tok prema bazi je prelazi. Ova konfiguracija nije utvrđena za Fakturis.
- **Poseban tim za bazu:** odvojeni DBA tim može biti razlog za granicu ako ima zasebne privilegije i sprovodi drugačija pravila pristupa ili administracije. Sama organizaciona podela timova, bez razlike u pravima i kontrolama, ne zahteva automatski granicu.

Različiti uređaji ne znače nužno različite zone, a jedna mašina može sadržati više zona ako su procesi ili nalozi odvojeni različitim privilegijama i kontrolama. Granica se postavlja prema tim razlikama, ne prema fizičkom rasporedu komponenti.

