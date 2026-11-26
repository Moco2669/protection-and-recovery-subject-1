---
tip: pojam
aliases: [nonce, number used once, inicijalizacioni vektor, initialization vector, IV]
izvor: 'NIST CSRC Glossary, nonce'
status: prihvaćeno
sloj: jezgro
---
# Jednokratna vrednost (nonce)

## Definicija
Jednokratna vrednost (nonce) je vrednost koja se, zajedno sa ključem, daje kao ulaz algoritmu šifrovanja, [[Digitalni potpis|potpisa]] ili [[Protokol|protokolu]] i koja se uz isti ključ sme upotrebiti samo jednom.

## Primer
Aplikacija AES-GCM-om šifruje broj računa svakog kupca u [[Baza podataka|bazi]], istim ključem iz [[Skladište tajni|skladišta tajni]]. Za svaki zapis pravi novu jednokratnu vrednost od 12 bajtova i čuva je otvoreno ispred šifrata. Isti broj računa upisan dva puta daje dva potpuno različita šifrata.

## Napomene
- Pri šifrovanju obezbeđuje da isti otvoreni tekst šifrovan istim ključem svaki put da drugačiji šifrat. Tada nije tajna: zapisuje se otvoreno pored šifrata, a bitno je samo da se uz isti ključ ne ponovi.
- Kod [[Kriptografija eliptičkih krivih#Potpisi na krivama|ECDSA]] je strožije: jednokratna vrednost mora biti i tajna i nepredvidiva.
- Razlika od [[Heširanje lozinki#So|soli]] objašnjena je u odeljku o soli.
- Inicijalizacioni vektor (IV) je jednokratna vrednost u [[Blokovska šifra#Režimi rada|režimu rada blokovske šifre]]. CBC traži nepredvidiv IV, CTR i GCM jedinstven. Brojač je jedinstven, ali predvidiv.
- Slučajna vrednost od 96 bita može da se ponovi posle mnogo poruka, pa NIST SP 800-38D ograničava AES-GCM sa slučajnim nonce-om na 2^32 šifrovanja jednim ključem.
- U protokolima jednokratna vrednost sprečava i ponavljanje starih poruka.
- Posledice ponavljanja su teške: kod protočnog šifrovanja otkriva se sadržaj ([[Protočna šifra]]), kod GCM-a i mogućnost lažiranja ([[Autentifikovano šifrovanje]]), kod [[Kriptografija eliptičkih krivih#Potpisi na krivama|ECDSA]] privatni ključ.

## Česti propusti i zaštita
- **Fiksni IV u kodu** (`iv = bytes(16)`): isti za sve poruke (CWE-329). *Zaštita:* nova vrednost za svako šifrovanje, iz [[Kriptografski generator slučajnih brojeva|kriptografskog generatora]] ili brojača.
- **Brojač koji se vrati na nulu** posle restarta programa, a ključ ostane isti. *Zaštita:* trajno čuvanje brojača ili novi ključ po pokretanju.
