---
tip: pojam
aliases: [key derivation function, KDF, HKDF, izvođenje ključa]
izvor: 'IETF RFC 5869, HKDF (https://www.rfc-editor.org/rfc/rfc5869.html); NIST SP 800-108 Rev. 1; NIST SP 800-56C Rev. 2'
status: prihvaćeno
sloj: jezgro
---
# Funkcija za izvođenje ključa (key derivation function, KDF)

## Definicija
Funkcija za izvođenje ključa je funkcija koja iz tajne vrednosti visoke nepredvidivosti (na primer rezultata [[Diffie-Hellman razmena ključeva|razmene ključeva]]) i javne oznake namene izračunava ključ, tako da su ključevi izvedeni za različite namene međusobno nezavisni i da nijedan ne otkriva polaznu tajnu.

## Primer
Posle [[Diffie-Hellman razmena ključeva|razmene ključeva]] u [[TLS|TLS 1.3]] obe strane imaju istu zajedničku tajnu. Iz nje HKDF izvodi poseban ključ za smer klijent → server, poseban za server → klijent i posebne ključeve za rukovanje. Tajna sama nikad ne služi kao ključ za šifrovanje.

## Napomene
- HKDF (RFC 5869) prvo „izdvaja“ ključ punog kvaliteta iz tajne koja nije ravnomerno slučajna, na primer rezultata DH razmene, pa ga „proširuje“ u ključeve za različite namene, uz oznaku namene (npr. `"sifrovanje-v1"`, `"mac-v1"`).
- Sirova zajednička tajna nije ključ: nije ravnomerno slučajna i jedna je, a potrebno je više ključeva.
- U [[Hibridna razmena ključeva|hibridnoj razmeni ključeva]] se upravo ovde spajaju dve tajne, klasična i postkvantna.
- Funkcije za izvođenje ključa iz lozinke (PBKDF2, Argon2) su zasebna, namerno spora vrsta, jer lozinka ima malo nepredvidivosti ([[Heširanje lozinki]]). NIST ih takođe razdvaja: SP 800-108 i SP 800-56C za ključeve i zajedničke tajne, SP 800-132 za lozinke.

## Česti propusti i zaštita
- **Isti ključ za šifrovanje i MAC**, ili za dva sistema. Propust u jednoj upotrebi tada ugrožava drugu. *Zaštita:* posebni ključevi izvedeni HKDF-om sa različitom oznakom namene.
- **Ključ izveden iz lozinke brzom funkcijom** (`SHA256(lozinka)` kao AES ključ): pogađa se kao heš lozinke. *Zaštita:* Argon2id ili PBKDF2 sa velikim brojem iteracija.
