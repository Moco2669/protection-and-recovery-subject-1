---
tip: pojam
aliases: [hybrid key exchange, hybrid key establishment, postkvantni hibrid, PQ/T hybrid]
izvor: 'IETF RFC 9954, Hybrid Key Exchange in TLS 1.3 (2026); IETF RFC 10024, Post-Quantum Traditional (PQ/T) Hybrid Key Agreement Mechanisms for TLS 1.3 (2026)'
status: prihvaćeno
sloj: front
---
# Hibridna razmena ključeva (hybrid key exchange)

## Definicija
Hibridna razmena ključeva je uspostavljanje zajedničkog ključa u kojem strane istovremeno izvode jednu klasičnu razmenu (npr. X25519) i jednu [[Postkvantna kriptografija|postkvantnu]] (npr. ML-KEM), a obe dobijene tajne zajedno ulaze u [[Funkcija za izvođenje ključa|funkciju za izvođenje ključa]], tako da napadač mora da razbije obe razmene da bi dobio ključ.

## Primer
TLS grupa X25519MLKEM768: tajna iz [[Diffie-Hellman razmena ključeva|X25519]] razmene i tajna iz [[Mehanizam enkapsulacije ključa#ML-KEM|ML-KEM-768]] enkapsulacije zajedno ulaze u [[Funkcija za izvođenje ključa|HKDF]]. Kvantni računar razbija X25519, ali ne ML-KEM; eventualna klasična slabost ML-KEM-a ne pomaže protiv X25519. Chrome (od verzije 131) i Firefox (od verzije 132) ovu grupu podrazumevano nude od kraja 2024, pa se velik deo današnjeg HTTPS saobraćaja već uspostavlja hibridno. Tok poruka prikazan je u [[TLS#Primer|primeru TLS rukovanja]].

## Napomene
- Razlog: postkvantni algoritmi su mladi (SIKE je razbijen klasično), a klasični su provereni, ali kvantno ugroženi. Hibrid ne traži da se bira.
- Cena: oko 1,2 KB više u svakom smeru tokom rukovanja.
- OpenSSH od verzije 9.0 (2022) podrazumevano koristi hibrid NTRU Prime + X25519, a od verzije 10.0 (2025) hibrid ML-KEM + X25519.
- Nije isto što i [[Hibridno šifrovanje]] (asimetrično + simetrično).

## Česti propusti i zaštita
- **Sopstveno kombinovanje tajni** (npr. XOR) umesto propisanog spajanja obe tajne u KDF zajedno sa porukama rukovanja: za takvu kombinaciju nema dokaza da je ključ bezbedan dok god je bar jedna razmena bezbedna. *Zaštita:* kombinovanje kako ga propisuje standard.
- **Degradiranje na samo klasičnu razmenu** uklanjanjem hibridne grupe iz ponude ([[Napad degradiranjem verzije]]). *Zaštita:* potpis nad porukama rukovanja, kao u TLS 1.3.
