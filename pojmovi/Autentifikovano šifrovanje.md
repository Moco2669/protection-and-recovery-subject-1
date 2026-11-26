---
tip: pojam
aliases: [authenticated encryption, AEAD, authenticated encryption with associated data, pridruženi podaci, associated data]
izvor: 'IETF RFC 5116, An Interface and Algorithms for Authenticated Encryption'
status: prihvaćeno
sloj: jezgro
---
# Autentifikovano šifrovanje (authenticated encryption with associated data, AEAD)

## Definicija
Autentifikovano šifrovanje (AEAD) je [[Simetrična kriptografija|simetrični]] algoritam koji uz šifrovanje poruke pravi i [[Kod za autentifikaciju poruke|oznaku autentičnosti]] nad šifratom i dodatnim nešifrovanim podacima (pridruženi podaci), tako da dešifrovanje vraća otvoreni tekst samo ako nisu menjani ni šifrat, ni pridruženi podaci, ni [[Jednokratna vrednost|jednokratna vrednost]], ni oznaka, a inače samo grešku.

## Primer
Aplikacija u [[Baza podataka|bazi]] čuva šifrovan broj računa svakog kupca. Bez pridruženih podataka, napadač sa pravom upisa u bazu (ali bez ključa) može da kopira šifrovan broj iz svog reda u red žrtve: šifrat je ispravan i dešifruje se, pa novac žrtve odlazi na račun napadača. Kada se identifikator reda navede kao pridruženi podatak, premešten šifrat ne prolazi proveru.

## Napomene
- Ulazi su ključ, [[Jednokratna vrednost|nonce]], otvoreni tekst i pridruženi podaci; izlaz je šifrat sa oznakom. Dešifrovanje vraća ceo tekst ili grešku, nikad neproveren rezultat.
- Algoritmi: AES-GCM i ChaCha20-Poly1305. TLS 1.3 dozvoljava samo AEAD.
- AEAD uklanja padding oracle ([[Blokovska šifra]]) i izmenu šifrata ([[Protočna šifra]]), pa je podrazumevani izbor za simetrično šifrovanje.

## Česti propusti i zaštita
- **Ponovljen nonce kod GCM-a** otkriva XOR dve poruke i ključ za oznake, pa napadač pravi lažne poruke koje prolaze proveru. *Zaštita:* brojač, novi ključ po poruci izveden [[Funkcija za izvođenje ključa|HKDF-om]], ili AES-GCM-SIV (RFC 8452), kod kojeg ponovljen nonce otkriva samo da su dve poruke iste.
- **Korišćenje teksta pre provere oznake** u bibliotekama koje dešifruju u delovima. *Zaštita:* ništa se ne obrađuje dok provera ne prođe.
- **Skraćena oznaka** (4 ili 8 bajtova) olakšava lažiranje. *Zaštita:* puna oznaka od 16 bajtova.
