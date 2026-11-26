---
tip: pojam
aliases: [password hashing, čuvanje lozinki, biber, pepper, so, salt, kriptografska so, probijanje heševa lozinki, offline password cracking, password cracking, probijanje lozinki, rainbow tabela, rainbow table, napad rečnikom, dictionary attack]
izvor: 'OWASP Password Storage Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html; NIST SP 800-63B-4; NIST CSRC Glossary, salt; MITRE ATT&CK T1110.002, Brute Force: Password Cracking'
status: prihvaćeno
sloj: jezgro
---
# Heširanje lozinki (password hashing)

## Definicija
Heširanje lozinki je način čuvanja lozinki u kojem se umesto lozinke čuva izlaz namerno skupe funkcije (spore, a često i memorijski zahtevne) izračunat iz lozinke i [[Heširanje lozinki#So|soli]], tako da sistem može da proveri unetu lozinku, a onaj ko pročita sačuvane vrednosti može lozinku da dobije samo skupim pogađanjem.

## Primer
Ista lozinka `Proleće2026!` sačuvana na tri načina u tabeli naloga:

```text
md5        3f0a9c...e1            brz heš, bez soli
sha256     9b71d2...4c            brz heš, bez soli
argon2id   $argon2id$v=19$m=19456,t=2,p=1$Zx8q...$J8f...Qk
```

Prva dva zapisa napadač proverava desetinama milijardi pokušaja u sekundi, a ista lozinka uvek daje isti zapis. Treći sadrži algoritam, parametre (19 MiB memorije, 2 prolaza, 1 nit), so i heš. Pri prijavi aplikacija iz zapisa čita parametre i so, ponovi računanje nad unetom lozinkom i poredi rezultat.

## Napomene
- Funkcije za lozinke: **Argon2id** (prvi izbor po OWASP-u), **scrypt**, **bcrypt** (ulaz do 72 bajta), **PBKDF2** (kada je potrebna FIPS usklađenost, uz mnogo iteracija).
- Argon2id i scrypt traže mnogo memorije po pokušaju, pa grafičke kartice gube prednost.
- **Biber (pepper)**: dodatna tajna, ista za sve naloge, van baze, npr. u [[Skladište tajni|skladištu tajni]]. Ako procuri samo baza, pogađanje ne može ni da počne. Biber je tajan i zajednički; so je javna i različita za svaki zapis.
- Zapis nosi algoritam i parametre, pa se posle uspešne prijave stari zapis zamenjuje jačim ([[Kriptografska agilnost]]).
- Iste funkcije (PBKDF2, Argon2) služe i za izvođenje ključa iz lozinke, npr. pri šifrovanju datoteke lozinkom ([[Funkcija za izvođenje ključa]]).
- Heširanje ne štiti od pogađanja preko forme za prijavu; tu pomažu ograničenje pokušaja i drugi faktor.

## So
So je javna slučajna vrednost, jedinstvena za svaki sačuvani zapis lozinke, koja se dodaje lozinki pre izračunavanja [[Kriptografska heš funkcija|heš funkcije]] i čuva otvoreno uz rezultat, tako da napadač ne može jedno izračunavanje da iskoristi za više naloga niti da ga obavi unapred.

Dva korisnika imaju istu lozinku `Proleće2026!`. Zbog različitih soli od po 16 bajtova njihovi zapisi se potpuno razlikuju, pa napadač koji ukrade bazu ne vidi da je lozinka ista i mora da je pogađa posebno za svaki nalog.

- So nije tajna; bez nje se lozinka ne bi mogla proveriti.
- So ne usporava pogađanje jedne lozinke. Brz heš sa solju je i dalje brz; so ide uz sporu funkciju, ne umesto nje.
- **Razlika od [[Jednokratna vrednost|jednokratne vrednosti]].** Obe su javne, obično slučajne i sprečavaju napade koji bi inače bili mogući, ali se razlikuju po upotrebi i po posledici ponavljanja. So se čuva trajno uz zapis lozinke i sprečava unapred izračunate napade; slučajno ponovljena so je bezopasna (napadač samo te dve lozinke pogađa zajedno), a štetna je tek ista so za sve naloge. Jednokratna vrednost prati poruku i mora biti jedinstvena u zadatom opsegu (uz isti ključ, u jednoj sesiji); jedno ponavljanje može da otkrije sadržaj ili ključ, a u protokolima omogućava ponavljanje stare poruke.

## Probijanje heševa lozinki
Probijanje heševa lozinki je napad u kojem napadač, pošto pribavi sačuvane heševe lozinki, na sopstvenoj opremi računa heševe velikog broja mogućih lozinki i poredi ih sa pribavljenim, dok ne nađe lozinke koje im odgovaraju.

LinkedIn je 2012. izgubio heševe lozinki: SHA-1 bez soli. Oko 6,5 miliona heševa objavljeno je na forumu, a više od polovine probijeno je za oko jedan dan. Napadači su zatim te lozinke isprobavali na drugim servisima istih korisnika.

- Napad je offline: ne prolazi kroz formu za prijavu, pa ga ne zaustavljaju zaključavanje naloga ni ograničenje pokušaja, i ne ostavlja [[Skladište zapisa|zapise]] na napadnutom sistemu.
- **Napad rečnikom** isprobava poznate lozinke i varijacije („reč + godina + !“) i u praksi je uspešniji od isprobavanja svih kombinacija.
- **Rainbow tabela** je tabela izračunata unapred, za jednu heš funkciju, iz koje se za dati heš brzo nalazi lozinka; umesto svih parova lozinka–heš čuva samo početke i krajeve dugih lanaca heširanja, pa zauzima mnogo manje prostora. So je čini beskorisnom, jer bi za svaku vrednost soli trebala posebna tabela.
- Jedna grafička kartica (RTX 4090, hashcat) računa oko 160 milijardi MD5 i oko 50 milijardi SHA-1 heševa u sekundi. Za Argon2id sa preporučenim parametrima taj broj je za mnogo redova veličine manji, jer svaki pokušaj traži desetine MiB memorije.
- Heševi obično procure drugim napadom: krađom rezervne kopije, SQL injekcijom ili kopijom baze ostavljenom u repozitorijumu.
- Odbijanje lozinki sa spiskova procurelih lozinki i drugi faktor smanjuju vrednost probijene lozinke.

## Česti propusti i zaštita
- **Šifrovanje umesto heširanja.** Adobe je 2013. izgubio oko 150 miliona naloga sa lozinkama šifrovanim 3DES-om u ECB režimu, bez soli: iste lozinke imale su iste šifrate, a pored njih su bili otvoreni podsetnici. Najčešće lozinke su pročitane bez ključa. *Zaštita:* lozinka se hešira, ne šifruje; ko ima ključ, ima sve lozinke.
- **Brz heš i heš bez soli** (CWE-759, CWE-916). *Zaštita:* Argon2id sa solju i preporučenim parametrima.
- **Sopstvena konstrukcija** (MD5 ponovljen 1000 puta). *Zaštita:* standardna funkcija iz biblioteke.
- **Korisničko ime ili identifikator kao so**: predvidivi su i isti na drugim sistemima. *Zaštita:* slučajna so iz [[Kriptografski generator slučajnih brojeva|kriptografskog generatora]] (obično 16 bajtova), nova pri svakoj promeni lozinke. Biblioteke za Argon2id i bcrypt same prave so.
- **Jedna so za sve naloge** vraća problem identičnih heševa. *Zaštita:* so po nalogu; tajna zajednička vrednost je biber, ne so.
