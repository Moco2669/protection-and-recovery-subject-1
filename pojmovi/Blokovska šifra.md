---
tip: pojam
aliases: [block cipher, blok šifra, AES, Advanced Encryption Standard, režim rada blokovske šifre, režim rada, block cipher mode of operation, mode of operation]
izvor: 'NIST FIPS 197 (ažurirano 2023), Advanced Encryption Standard: https://doi.org/10.6028/NIST.FIPS.197-upd1; NIST SP 800-38A'
status: prihvaćeno
sloj: jezgro
---
# Blokovska šifra (block cipher)

## Definicija
Blokovska šifra je [[Simetrična kriptografija|simetrični]] algoritam koji ključem preslikava blok otvorenog teksta fiksne dužine u blok šifrata iste dužine, tako da se istim ključem preslikavanje može obrnuti, a bez ključa je ono nepredvidivo.

## Primer
AES šifruje blokove od 16 bajtova. PDF od 80 KB ima oko pet hiljada takvih blokova; sama šifra ne određuje kako se oni povezuju, niti šta se radi sa poslednjim, nepotpunim blokom. To određuje režim rada.

## Napomene
- **AES** (NIST FIPS 197, 2001) je današnji standard: blok od 16 bajtova, ključ od 128, 192 ili 256 bita. Nije poznat napad na AES bitno brži od isprobavanja ključeva. Isti AES može da bude bezbedan (GCM) ili da otkriva sadržaj (ECB), zavisno od režima.
- DES ima ključ od samo 56 bita i razbija se isprobavanjem. 3DES ima blok od 8 bajtova, pa je posle velike količine podataka šifrovanih jednim ključem ranjiv napadom Sweet32 (2016); NIST ga je zabranio za šifrovanje od 2024.
- AES-256 se bira za podatke koji moraju ostati tajni decenijama, kao rezerva prema kvantnim računarima ([[Postkvantna kriptografija]]).

## Režimi rada
Režim rada blokovske šifre je pravilo po kojem se blokovska šifra, koja sama šifruje tačno jedan blok, primenjuje na poruku proizvoljne dužine: kako se uzastopni blokovi obrađuju i međusobno povezuju. Neki režimi (GCM) uz šifrat daju i oznaku autentičnosti.

| Režim | Kako radi | Kada |
| --- | --- | --- |
| ECB | blokovi nezavisno | nikad za podatke |
| CBC | blok se XOR-uje sa prethodnim šifratom | stari sistemi; traži nepredvidiv IV i poseban MAC |
| CTR | šifruje se brojač, rezultat se XOR-uje sa tekstom | radi kao [[Protočna šifra\|protočna šifra]]; traži jedinstven nonce |
| GCM | CTR + oznaka autentičnosti | podrazumevani izbor ([[Autentifikovano šifrovanje]]) |

ECB, CBC i CTR štite samo poverljivost; uz njih ide [[Kod za autentifikaciju poruke|MAC]] nad šifratom, proveren pre dešifrovanja.

U ECB režimu svaki blok se šifruje nezavisno, pa isti blokovi daju isti šifrat. Poznata slika pingvina šifrovana u ECB-u to pokazuje: obrisi ostaju vidljivi. Na isti način se iz lozinki šifrovanih u ECB-u vidi koji korisnici imaju istu lozinku ([[Heširanje lozinki#Česti propusti i zaštita|šifrovanje umesto heširanja]]).

## Česti propusti i zaštita
- **„Koristimo AES-256“ kao dokaz bezbednosti.** Greške su po pravilu u režimu, [[Jednokratna vrednost|jednokratnoj vrednosti]] i čuvanju ključa, ne u AES-u. *Zaštita:* AES u [[Autentifikovano šifrovanje|autentifikovanom režimu]] (GCM) i ključ van koda.
- **ECB kao podrazumevani režim.** U Javi `Cipher.getInstance("AES")` kod uobičajenih provajdera znači ECB. *Zaštita:* režim se uvek navodi izričito, npr. `AES/GCM/NoPadding`.
- **Padding oracle (CBC).** Server različito odgovara na šifrat sa neispravnom dopunom (padding) i na šifrat sa ispravnom dopunom, ali pogrešnim sadržajem (druga greška ili drugo vreme obrade, vidi [[Napad merenjem vremena]]). Slanjem izmenjenih šifrata napadač dešifruje poruku bajt po bajt, bez ključa (Vaudenay 2002; ASP.NET 2010; POODLE 2014). *Zaštita:* autentifikovano šifrovanje, ili provera MAC-a pre dešifrovanja i jedinstvena poruka o grešci.
- **Predvidiv ili fiksan IV u CBC-u** otkriva da li dve poruke počinju isto (CWE-329). *Zaštita:* slučajan IV za svaku poruku.
