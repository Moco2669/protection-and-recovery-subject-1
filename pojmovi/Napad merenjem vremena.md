---
tip: pojam
aliases: [timing attack, timing side-channel attack, napad vremenskim kanalom]
izvor: 'MITRE CWE-208, Observable Timing Discrepancy: https://cwe.mitre.org/data/definitions/208.html; Kocher, Timing Attacks on Implementations of Diffie-Hellman, RSA, DSS, and Other Systems, CRYPTO 1996'
status: prihvaćeno
sloj: jezgro
---
# Napad merenjem vremena (timing attack)

## Definicija
Napad merenjem vremena je napad u kojem napadač iz merenja koliko dugo traje obrada njegovih zahteva zaključuje o tajnim podacima koje ta obrada koristi, na primer o ključu ili ispravnoj vrednosti [[Kod za autentifikaciju poruke|oznake]].

## Primer
Server proverava MAC oznaku od 32 bajta običnim poređenjem, koje se prekida na prvom različitom bajtu. Napadač šalje zahteve sa svih 256 vrednosti prvog bajta i meri odgovore: vrednost kod koje odgovor stiže malo kasnije je ispravna, jer je poređenje prešlo na drugi bajt. Ponavljanjem bajt po bajt pogađa celu oznaku, umesto da isprobava 2^256 mogućnosti.

## Napomene
- Algoritam može biti ispravan, a implementacija ipak da otkriva tajnu: ako trajanje zavisi od tajnih podataka (grananje, rano prekidanje petlje, deljenje), vreme postaje sporedni kanal (side channel).
- Razlike su često vrlo male, ali se ponavljanjem i statistikom mogu izmeriti i preko mreže; Lucky Thirteen je tako napadao TLS.
- Zaštita je implementacija u **konstantnom vremenu**: trajanje ne zavisi od tajnih vrednosti. Zato se koriste proverene biblioteke, a ne sopstvena implementacija.

## Gde se javlja
| Mesto | Šta curi | Beleška |
| --- | --- | --- |
| poređenje MAC oznake bajt po bajt | ispravna oznaka, bajt po bajt | [[Kod za autentifikaciju poruke]] |
| obrada neispravne CBC dopune (padding) u TLS-u (Lucky Thirteen, 2013) | sadržaj poruke | [[Blokovska šifra]], [[TLS]] |
| operacije sa tajnim skalarom k na eliptičkoj krivoj | privatni ključ | [[Kriptografija eliptičkih krivih]] |
| deljenje zavisno od tajnih podataka u Kyber-u (KyberSlash, 2023–2024) | privatni ključ | [[Mehanizam enkapsulacije ključa#ML-KEM\|ML-KEM]] |

## Zaštita
- Tajne vrednosti se ne porede običnim `==`, nego funkcijom za poređenje u konstantnom vremenu (`hmac.compare_digest`, `crypto.timingSafeEqual`).
- Svaki neispravan ulaz daje istu grešku i prolazi isti put obrade, bez obzira na to da li je neispravna dopuna ili oznaka; još bolje je [[Autentifikovano šifrovanje]].
