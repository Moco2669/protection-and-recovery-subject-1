---
tip: pojam
aliases: [symmetric cryptography, symmetric-key cryptography, simetrično šifrovanje, tajni ključ, secret key]
izvor: 'NIST SP 800-175B Rev. 1, odeljak 3; NIST CSRC Glossary, symmetric key'
status: prihvaćeno
sloj: temelj
---
# Simetrična kriptografija (symmetric cryptography)

## Definicija
Simetrična kriptografija je skup algoritama za šifrovanje i proveru autentičnosti podataka u kojima se isti tajni ključ koristi za obe suprotne operacije: za šifrovanje i dešifrovanje, odnosno za pravljenje i proveru [[Kod za autentifikaciju poruke|oznake autentičnosti]].

## Primer
Tokom [[TLS]] veze pregledač šifruje zahtev AES-om ključem za smer klijent → server, a server ga dešifruje istim tim ključem. Odgovore server šifruje drugim ključem, za suprotan smer, koji takođe imaju obe strane. Nijedan ključ nije poslat mrežom: obe strane su ih izračunale iz zajedničke tajne dobijene [[Diffie-Hellman razmena ključeva|razmenom ključeva]] ([[Funkcija za izvođenje ključa]]).

## Napomene
- Vrste i njihov odnos:

```text
simetrična kriptografija
├── blokovska šifra (AES): šifruje jedan blok od 16 bajtova
│     └── režim rada (ECB, CBC, CTR, GCM): kako se blokovska šifra
│         primenjuje na celu poruku; CTR i GCM od nje prave
│         ključni niz, pa rade kao protočna šifra
├── protočna šifra (ChaCha20)
└── kod za autentifikaciju poruke (HMAC)
```

  Vidi [[Blokovska šifra]], [[Protočna šifra]] i [[Kod za autentifikaciju poruke]]. AES sam šifruje samo jedan blok; poruku šifruje tek AES u nekom režimu, na primer AES-GCM ([[Autentifikovano šifrovanje]]).
- Brza je i ima kratke ključeve; 128 bita je danas dovoljno, a za podatke koji moraju ostati tajni decenijama bira se AES-256 ([[Postkvantna kriptografija]]).
- Glavni problem je raspodela ključa: kako da dve strane koje se nisu srele dobiju isti tajni ključ? To rešava [[Asimetrična kriptografija|asimetrična kriptografija]], pa se u praksi kombinuju, kao u [[TLS|TLS-u]] i [[Hibridno šifrovanje|hibridnom šifrovanju]].
- Kvantni računar je simetričnoj kriptografiji mnogo manja pretnja nego asimetričnoj ([[Postkvantna kriptografija]]).

## Česti propusti i zaštita
- **Jedan ključ za sve klijente.** Ključ ugrađen u mobilnu aplikaciju može da izvuče svako ko preuzme aplikaciju, pa se njime predstavlja kao bilo koji korisnik. *Zaštita:* tajna ne ide na uređaj korisnika; svaki klijent dobija sopstveni, ograničen pristupni token koji se može opozvati.
