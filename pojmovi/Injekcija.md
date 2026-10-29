---
tip: pojam
aliases: [injection, SQL injekcija, SQL injection, XSS, cross-site scripting]
izvor: OWASP Top 10:2025, A05:2025 Injection (https://owasp.org/Top10/2025/); CWE-74, CWE-89, CWE-79
status: predlog
sloj: jezgro
---
# Injekcija (injection)

## Definicija
Injekcija je [[Ranjivost|ranjivost]] [[Komponenta sistema|komponente sistema]], najčešće [[Web aplikacija|web aplikacije]], u kojoj komponenta ugrađuje ulazne podatke koje može da kontroliše neko drugi u naredbu, upit ili stranicu koju zatim izvršava ili prikazuje, bez razdvajanja podataka od naredbe, pa se delovi ulaza izvršavaju kao deo naredbe.

## Primer
Pretraga kupaca u aplikaciji [[Fakturis]] sastavlja upit ovako:

```sql
SELECT * FROM kupci WHERE korisnik_id = 17 AND naziv LIKE '%<tekst pretrage>%'
```

Ako korisnik u polje pretrage upiše `' OR '1'='1' --`, uslov o vlasniku prestaje da važi i aplikacija vraća kupce svih korisnika. To je SQL injekcija.

Polje „napomena“ na fakturi prikazuje se na javnoj stranici za plaćanje bez kodiranja. Ako izdavalac u napomenu upiše `<script>`, skripta se izvršava u pregledaču kupca koji otvori stranicu i može, na primer, da preusmeri unos kartice na lažnu stranicu. To je skriptovanje između sajtova (cross-site scripting, XSS).

## Napomene
- Kod SQL injekcije naredba se izvršava na serveru, a kod XSS-a u pregledaču druge osobe. OWASP ih svrstava u istu kategoriju jer imaju isti uzrok: podaci i naredba nisu razdvojeni.
- Odgovarajuće kontrole su parametrizovani upiti za SQL i kodiranje izlaza za HTML. Sama provera ulaza obično nije dovoljna.
