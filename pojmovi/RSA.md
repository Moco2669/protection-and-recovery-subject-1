---
tip: pojam
aliases: [Rivest–Shamir–Adleman, RSA-OAEP, RSA-PSS, PKCS#1]
izvor: 'IETF RFC 8017, PKCS #1: RSA Cryptography Specifications Version 2.2 ([RFC](https://www.rfc-editor.org/rfc/rfc8017.html)); NIST FIPS 186-5'
status: prihvaćeno
sloj: jezgro
---
# RSA (Rivest–Shamir–Adleman)

## Definicija
RSA je [[Asimetrična kriptografija|asimetrični]] algoritam u kojem je javni ključ par (n, e), gde je n proizvod dva velika prosta broja, a privatni ključ eksponent d, i u kojem se šifrovanje i [[Digitalni potpis|potpis]] svode na stepenovanje po modulu n. Iz javnog ključa d se može izračunati samo ako se n rastavi na činioce, pa bezbednost počiva na teškoći tog rastavljanja.

## Primer
Sa malim brojevima, samo radi ilustracije: p = 61, q = 53, pa je n = 3233. Javni eksponent je e = 17, a iz p i q se računa privatni eksponent d = 2753. Poruka m = 65 šifruje se kao `65^17 mod 3233 = 2790`, a `2790^2753 mod 3233` vraća 65. Ko rastavi 3233 na 61 · 53, izračuna d. Za n od 2048 bita to nije izvodljivo.

## Napomene
- Javni ključ je (n = p·q, e); privatni eksponent d računa se iz p i q. Šifrovanje `c = m^e mod n`, dešifrovanje `m = c^d mod n`.
- Koristi se za potpis i za šifrovanje kratkih podataka, najčešće ključeva.
- „Udžbenički RSA“ (samo stepenovanje) je nebezbedan; koristi se šema za padding: OAEP za šifrovanje, PSS za potpis.
- Ključ najmanje 2048 bita; 3072 bita daje oko 128 bita bezbednosti, kao [[Kriptografija eliptičkih krivih|ECC]] od 256 bita.
- TLS 1.3 je uklonio RSA prenos ključa, jer nema [[Savršena tajnost unapred|tajnost unapred]]; RSA tu služi samo za potpis servera. Kvantni računar razbija RSA ([[Postkvantna kriptografija]]).

## Česti propusti i zaštita
- **Bleichenbacherov napad (1998).** Server koji za RSA šifrovanje po starom PKCS#1 v1.5 različito odgovara na neispravan i ispravan padding postaje „orakl“: napadač slanjem mnogo izmenjenih šifrata dešifruje tajnu. *Zaštita:* OAEP, ili [[Mehanizam enkapsulacije ključa|KEM]] umesto RSA šifrovanja.
- **Kratki ključevi.** U napadu FREAK (2015) istraživači su RSA ključ od 512 bita rastavili za oko 7,5 sati u oblaku ([[Napad degradiranjem verzije]]). *Zaštita:* najmanje 2048 bita i isključeni stari režimi.
- **Prosti brojevi previše blizu jedan drugom.** Ako su p i q blizu, n se rastavlja Fermatovom metodom iz 1643: n = a² − b² = (a − b)(a + b), gde je a = (p + q)/2 tek nešto veće od √n. Probaju se a = ⌈√n⌉, ⌈√n⌉ + 1, … dok a² − n ne bude potpun kvadrat b². Na primer, za n = 9991 je √n ≈ 99,95, pa a = 100 daje 10000 − 9991 = 9 = 3², odnosno p = 97 i q = 103, u jednom koraku. Hanno Böck je 2022. ovako rastavio RSA ključeve Canon i Fujifilm štampača: biblioteka Rambus SafeZone je posle prvog prostog broja birala drugi u njegovoj blizini (CVE-2022-26320). *Zaštita:* p i q se biraju nezavisno, proverenom bibliotekom; ključevi napravljeni ranjivom bibliotekom se zamenjuju.
