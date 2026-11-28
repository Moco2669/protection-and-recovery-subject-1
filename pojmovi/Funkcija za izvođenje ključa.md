---
tip: pojam
aliases: [key derivation function, KDF, HKDF, izvođenje ključa]
izvor: 'NIST SP 800-108 Rev. 1; NIST SP 800-56C Rev. 2; NIST SP 800-132; IETF RFC 5869, HKDF (https://www.rfc-editor.org/rfc/rfc5869.html)'
status: prihvaćeno
sloj: jezgro
---
# Funkcija za izvođenje ključa (key derivation function, KDF)

## Definicija
Funkcija za izvođenje ključa je funkcija koja iz tajne vrednosti (rezultata [[Diffie-Hellman razmena ključeva|razmene ključeva]], drugog ključa ili lozinke) i javnih parametara, kao što su oznaka namene ili [[Heširanje lozinki#So|so]], izračunava jedan ili više ključeva, tako da su ključevi izvedeni za različite namene međusobno nezavisni i da nijedan ne otkriva polaznu tajnu.

## Primer
Posle [[Diffie-Hellman razmena ključeva|razmene ključeva]] u [[TLS|TLS 1.3]] obe strane imaju istu zajedničku tajnu. Iz nje HKDF izvodi poseban ključ za smer klijent → server, poseban za server → klijent i posebne ključeve za rukovanje. Tajna sama nikad ne služi kao ključ za šifrovanje.

Program za arhiviranje šifruje arhivu lozinkom koju korisnik unese: iz lozinke i nove slučajne soli Argon2id-om izvodi AES ključ, a so upisuje otvoreno uz arhivu.

## Napomene
- HKDF (RFC 5869) prvo „izdvaja“ ključ punog kvaliteta iz tajne koja nije ravnomerno slučajna, na primer rezultata DH razmene, pa ga „proširuje“ u ključeve za različite namene, uz oznaku namene (npr. `"sifrovanje-v1"`, `"mac-v1"`).
- Sirova zajednička tajna nije ključ: nije ravnomerno slučajna i jedna je, a potrebno je više ključeva.
- U [[Hibridna razmena ključeva|hibridnoj razmeni ključeva]] se upravo ovde spajaju dve tajne, klasična i postkvantna.
- Dve vrste, prema polaznoj tajni:
  - **iz tajne visoke nepredvidivosti** (zajednička tajna, drugi ključ): HKDF; brza, jer takva tajna ne može da se pogodi (NIST SP 800-108, SP 800-56C);
  - **iz lozinke** (password-based KDF): PBKDF2, scrypt, Argon2; namerno spora i sa solju, jer lozinka ima malo nepredvidivosti i pogađa se ([[Heširanje lozinki]], NIST SP 800-132).

## Česti propusti i zaštita
- **Isti ključ za šifrovanje i MAC**, ili za dva sistema. Propust u jednoj upotrebi tada ugrožava drugu. *Zaštita:* posebni ključevi izvedeni HKDF-om sa različitom oznakom namene.
- **Ključ izveden iz lozinke brzom funkcijom** (`SHA256(lozinka)` kao AES ključ): pogađa se kao heš lozinke. *Zaštita:* Argon2id ili PBKDF2 sa velikim brojem iteracija.
