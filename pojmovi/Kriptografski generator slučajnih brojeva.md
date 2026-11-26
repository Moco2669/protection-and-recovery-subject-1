---
tip: pojam
aliases: [cryptographically secure pseudorandom number generator, CSPRNG, DRBG, kriptografski bezbedan generator]
izvor: 'NIST SP 800-90A Rev. 1, Recommendation for Random Number Generation Using Deterministic Random Bit Generators'
status: prihvaćeno
sloj: temelj
---
# Kriptografski generator slučajnih brojeva (cryptographically secure random number generator)

## Definicija
Kriptografski generator slučajnih brojeva je program ili uređaj koji proizvodi niz bitova takav da se, ni uz poznavanje svih prethodnih izlaza, sledeći bit ne može praktično predvideti bolje nego slučajnim pogađanjem.

## Primer
Za link „zaboravljena lozinka“ aplikacija pravi token od 32 bajta iz generatora operativnog sistema (Python: `secrets.token_urlsafe(32)`). Ko vidi stotinu ranijih tokena, ne može da pogodi sledeći.

Kontraprimer: `Math.random()` i `java.util.Random` iz nekoliko izlaza otkrivaju unutrašnje stanje, pa napadač zatraži promenu lozinke za svoj nalog, vidi svoj token i izračuna token poslat žrtvi (CWE-338).

## Napomene
- Služi za pravljenje ključeva, [[Heširanje lozinki#So|soli]], [[Jednokratna vrednost|jednokratnih vrednosti]] i tokena.
- Pojam obuhvata i hardverske izvore slučajnosti i determinističke generatore koji iz malo slučajnosti prave dug niz (DRBG).
- Koristi se generator operativnog sistema (`getrandom()`, `/dev/urandom`, `BCryptGenRandom`) ili API jezika koji ga poziva (`secrets`, `SecureRandom`, `crypto.getRandomValues`).
- Ključ od 256 bita napravljen iz izvora sa milion mogućih stanja ima milion mogućnosti, ne 2^256.

## Česti propusti i zaštita
- **Debian OpenSSL (2006–2008, CVE-2008-0166).** Izmena koda u Debianovom paketu ostavila je identifikator procesa kao jedini promenljiv ulaz u seme, pa je za dati tip i dužinu ključa i arhitekturu postojalo samo 32.767 mogućih SSH i TLS ključeva. Svi su mogli da se izračunaju unapred. *Zaštita:* ne menjati kriptografski kod bez stručnog pregleda; posle otkrića svi takvi ključevi su morali biti zamenjeni.
- **Seme iz vremena.** Generator inicijalizovan trenutnim vremenom napadač pogađa isprobavanjem vremena oko trenutka pravljenja tokena. *Zaštita:* generator OS-a, bez ručnog semena.
- **Android `SecureRandom` (2013).** Androidov generator u određenim uslovima nije bio ispravno inicijalizovan i ponavljao je „slučajne“ vrednosti. Bitkoin novčanici na Androidu iz njega su uzimali tajni broj k za [[Kriptografija eliptičkih krivih#Potpisi na krivama|ECDSA]] potpise transakcija, a dva potpisa sa istim k otkrivaju privatni ključ. Pošto su sve transakcije javne, napadači su pretraživali lanac blokova tražeći ponovljen k i ukrali oko 55 BTC. *Zaštita:* ispravan generator OS-a; kod ECDSA i deterministički k (RFC 6979).
- **Generator sa zadnjim vratima: Dual_EC_DRBG.** NIST ga je standardizovao 2006. Koristi dve konstantne tačke P i Q na [[Kriptografija eliptičkih krivih|eliptičkoj krivoj]] P-256, čije poreklo nije objašnjeno. Shumow i Ferguson (Microsoft) pokazali su 2007. da onaj ko zna tajnu vezu između P i Q iz jednog izlaza izračunava stanje generatora i predviđa sve naredne izlaze, pa i ključeve napravljene od njih. Dokumenti koje je 2013. objavio Snowden ukazali su da je NSA vodila standardizaciju ovog generatora; da NSA zna tu vezu nije javno dokazano. NIST je generator povukao 2014. Da su ovakva zadnja vrata stvarno iskoristiva, pokazao je Juniper 2015: neko je u kodu njegovih VPN uređaja zamenio Q svojom tačkom i time mogao da pasivno dešifruje VPN saobraćaj; ko je to uradio, nije utvrđeno. *Zaštita:* generatori i konstante sa javno obrazloženim izborom.
