---
tip: pojam
aliases: [downgrade attack, napad snižavanjem verzije, version rollback attack, bidding-down attack]
izvor: 'MITRE CWE-757, Selection of Less-Secure Algorithm During Negotiation; IETF RFC 8446, odeljak 4.1.3'
status: prihvaćeno
sloj: jezgro
---
# Napad degradiranjem verzije (downgrade attack)

## Definicija
Napad degradiranjem verzije je napad u kojem napadač, menjajući ili ometajući pregovaranje između dve strane koje obe podržavaju jak [[Protokol|protokol]] ili algoritam, navodi strane da se dogovore o slabijem, koji zatim napada.

## Primer
FREAK (2015): mnogi serveri su, radi kompatibilnosti, i dalje podržavali „izvozne“ RSA ključeve od 512 bita iz devedesetih. Napadač na putanji menja ponudu klijenta tako da traži izvozni režim, a greška u klijentima (OpenSSL, Apple SecureTransport) dozvoljavala je da ga prihvate. Istraživači su ključ od 512 bita rastavili za oko 7,5 sati u oblaku, posle čega se veza može čitati. Ni klijent ni server nisu želeli slab algoritam; bilo je dovoljno da ga podržavaju.

## Napomene
- **POODLE (2014)** ima drugačiji uzrok: degradiranje je radio sam pregledač, namerno. Kada veza ne uspe, ponovo je pokušavao sa starijom verzijom, sve do SSL 3.0, radi kompatibilnosti sa starim serverima. Napadaču je bilo dovoljno da prekida veze, a SSL 3.0 je zatim imao padding oracle ([[Blokovska šifra]]). Rešenje je TLS_FALLBACK_SCSV (RFC 7507): pregledač pri ponovnom pokušaju javlja serveru da je spustio verziju, pa server koji podržava noviju odbija vezu. SSL 3.0 je posle toga isključen u pregledačima.
- TLS 1.3 potpisuje sve poruke rukovanja, pa se izmena ponude otkriva; server uz to označava kada pregovara stariju verziju.
- [[Kriptografska agilnost]] i degradiranje verzije su dve strane istog: izbor algoritma mora biti zaštićen od toga da ga napravi napadač.

## Zaštita
- Stari protokoli i algoritmi se uklanjaju, ne samo „ne koriste podrazumevano“.
- Pregovaranje je autentifikovano (potpis nad porukama rukovanja).
- Konfiguracija servera se periodično proverava alatom za skeniranje TLS podešavanja.
