---
tip: pojam
aliases: [harvest now decrypt later, HNDL, store now decrypt later]
izvor: 'NIST IR 8547, Transition to Post-Quantum Cryptography Standards (oktobar 2026); Mosca, Cybersecurity in an Era with Quantum Computers: Will We Be Ready?, IEEE Security & Privacy 16(5), 2018'
status: prihvaćeno
sloj: front
---
# Prikupi sada, dešifruj kasnije (harvest now, decrypt later, HNDL)

## Definicija
Prikupi sada, dešifruj kasnije je napad u kojem napadač danas pribavlja i čuva šifrovane podatke ili snimljen šifrovan saobraćaj koji ne može da dešifruje, da bi ih dešifrovao kada postane dostupno sredstvo koje razbija korišćenu kriptografiju, pre svega kvantni računar.

## Primer
Bolnica šalje elektronske kartone pacijenata preko TLS-a sa X25519 razmenom. Napadač koji danas snima taj saobraćaj ne može ništa da pročita. Ako za deset godina ima pristup dovoljno velikom kvantnom računaru, iz snimka izračuna ključeve i čita kartone, koji su i tada poverljivi. Šifrovanje je bilo ispravno, ali ne dovoljno dugo.

## Napomene
- **Moskina nejednakost:** ako je x koliko godina podaci moraju ostati tajni, y koliko traje prelaz na postkvantnu kriptografiju, a z za koliko godina će postojati kvantni računar dovoljne snage, onda su za x + y > z podaci već ugroženi.
- Ugrožena je poverljivost. Lažni potpisi biće mogući tek kada kvantni računar postoji, pa se razmena ključeva prevodi pre potpisa.
- [[Savršena tajnost unapred]] ne pomaže: napadač ne krade ključ, nego rešava samu razmenu iz snimka.

## Zaštita
- [[Hibridna razmena ključeva]] u TLS-u i SSH-u već danas.
- Hibridni klasično-postkvantni KEM u [[Hibridno šifrovanje|hibridnom šifrovanju]] podataka koji se dugo čuvaju (arhive, rezervne kopije).
- Manje podataka i kraći rok čuvanja: ono što ne postoji ne može se dešifrovati.
