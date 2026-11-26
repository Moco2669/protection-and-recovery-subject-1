---
tip: pojam
aliases: [post-quantum cryptography, PQC, kvantno otporna kriptografija]
izvor: 'NIST IR 8547, Transition to Post-Quantum Cryptography Standards (oktobar 2026); NIST FIPS 203, FIPS 204, FIPS 205 (avgust 2024)'
status: prihvaćeno
sloj: front
---
# Postkvantna kriptografija (post-quantum cryptography, PQC)

## Definicija
Postkvantna kriptografija je [[Asimetrična kriptografija|asimetrična kriptografija]] zasnovana na matematičkim problemima za koje nije poznat efikasan postupak rešavanja ni na klasičnom ni na kvantnom računaru, a koja radi na današnjim računarima.

## Primer
Firma danas uspostavlja TLS veze razmenom X25519 i potpisuje ažuriranja svog softvera ECDSA-om. Kada se pojavi kvantni računar dovoljne snage, napadač iz ranije snimljenih veza izračunava ključeve sesija, a ECDSA ključem potpisuje lažno ažuriranje kao da je od firme. AES-256 kojim su podaci u tim vezama šifrovani nije problem: ugrožena je razmena ključeva i potpis, ne simetrično šifrovanje.

## Napomene
- Prvo se prevodi razmena ključeva, jer je snimljeni saobraćaj ugrožen već danas ([[Prikupi sada dešifruj kasnije]]); ona se već uvodi [[Hibridna razmena ključeva|hibridno]] u TLS-u i SSH-u. Potpisi dolaze kasnije: lažni potpis je moguć tek kada kvantni računar postoji, a postkvantni potpisi su znatno veći.
- **Rokovi:** prema NIST IR 8547, kvantno ugroženi algoritmi su zastareli posle 2030, a zabranjeni posle 2035.
- Prelaz traži [[Kriptografska agilnost|agilnost]]: svaka razmena ključeva i svaki potpis u sistemu moraju moći da se zamene.
- Nije isto što i kvantna distribucija ključa (QKD), koja traži posebnu fizičku opremu. PQC je običan softver.

## Šta se menja
| Namena | Danas (razbija Šorov algoritam) | Postkvantna zamena (NIST, 2024) | Na čemu počiva | Gde se menja |
| --- | --- | --- | --- | --- |
| uspostavljanje ključa | [[RSA]] prenos ključa, [[Diffie-Hellman razmena ključeva\|DH]], ECDH (X25519) | [[Mehanizam enkapsulacije ključa#ML-KEM\|ML-KEM]] (FIPS 203), ranije Kyber | rešetke | TLS i SSH rukovanje, [[Hibridno šifrovanje\|hibridno šifrovanje]] |
| potpis | RSA, [[Kriptografija eliptičkih krivih#Potpisi na krivama\|ECDSA, EdDSA]] | ML-DSA (FIPS 204), ranije Dilithium; SLH-DSA (FIPS 205), ranije SPHINCS+ | rešetke; heš funkcije | sertifikati, potpis servera u TLS-u, potpisi ažuriranja |
| simetrično šifrovanje i heš | AES, SHA-256 samo oslabi Groverov algoritam | bez zamene, dovoljan je AES-256 | | |

- **Šorov algoritam** (1994) na kvantnom računaru efikasno rastavlja broj na činioce i rešava diskretni logaritam, pa razbija RSA, DH i ECC u potpunosti. Veći ključ ne pomaže.
- **Groverov algoritam** (1996) isprobavanje 2^n mogućnosti skraćuje na oko 2^(n/2) koraka. AES-128 se tako ponaša kao ključ od oko 64 bita, a AES-256 kao ključ od oko 128 bita, što je dovoljno.
- **Kako zamene utiču na sistem:** ML-KEM menja oblik razmene (KEM umesto DH) i povećava poruke rukovanja za oko 1,2 KB; ML-DSA povećava potpise i sertifikate (3309 bajtova naspram 64 kod Ed25519); SLH-DSA je sporiji i ima još veće potpise, ali počiva samo na heš funkcijama, pa mu je pretpostavka najkonzervativnija.
- Kao rezervni KEM iz druge porodice (kodovi za ispravljanje grešaka) NIST je 2025. izabrao HQC, za slučaj da se nađe slabost rešetki.

## Česti propusti i zaštita
- **Poverenje u nove algoritme bez rezerve.** Kandidat SIKE je 2022. razbijen klasičnim računarom za oko sat vremena, a iste godine i Rainbow. Implementacije ML-KEM-a imale su napade [[Napad merenjem vremena|merenjem vremena]] (KyberSlash). *Zaštita:* hibrid sa klasičnim algoritmom i proverene biblioteke.
- **„Nije hitno, kvantni računar još ne postoji.“** Za podatke koji moraju ostati tajni duže od vremena do njegove pojave, napad počinje danas ([[Prikupi sada dešifruj kasnije|Moskina nejednakost]]). *Zaštita:* procena po roku poverljivosti podataka, ne po verovatnoći.
