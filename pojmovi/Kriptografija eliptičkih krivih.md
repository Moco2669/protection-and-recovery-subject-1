---
tip: pojam
aliases: [elliptic curve cryptography, ECC, eliptička kriva, elliptic curve, ECDLP, problem diskretnog logaritma na eliptičkoj krivoj, ECDSA, Elliptic Curve Digital Signature Algorithm, EdDSA, Edwards-curve Digital Signature Algorithm]
izvor: 'NIST SP 800-186, Elliptic Curve Domain Parameters; Hankerson, Menezes, Vanstone, Guide to Elliptic Curve Cryptography, 2004; NIST FIPS 186-5, odeljci 6 i 7 (ECDSA i EdDSA)'
status: prihvaćeno
sloj: jezgro
---
# Kriptografija eliptičkih krivih (elliptic curve cryptography, ECC)

## Definicija
Kriptografija eliptičkih krivih je skup [[Asimetrična kriptografija|asimetričnih]] algoritama u kojima je privatni ključ tajni broj k, a javni ključ tačka k·G, dobijena k-strukim „sabiranjem“ javno poznate polazne tačke G na unapred izabranoj eliptičkoj krivoj, i u kojima bezbednost počiva na teškoći izračunavanja k iz G i k·G.

## Primer
Pri otvaranju HTTPS veze pregledač izabere tajni broj k od oko 255 bita i pošalje serveru tačku k·G na krivoj Curve25519, zapisanu u 32 bajta. Iz te tačke i javno poznate polazne tačke G niko ne može da izračuna k, a server svojom tačkom radi isto; od dve tačke obe strane dobijaju istu tajnu ([[Diffie-Hellman razmena ključeva|X25519]]).

## Napomene
| Bezbednost (bita) | Simetrično | RSA / klasični DH | ECC (najmanje) |
| --- | --- | --- | --- |
| 128 | 128 | 3072 | 256 |
| 192 | 192 | 7680 | 384 |
| 256 | 256 | 15360 | 512 |

Vrednosti prema NIST SP 800-57, Part 1, Rev. 5.

- Kratki ključevi i brze operacije razlog su što ECC danas preovlađuje u TLS-u i SSH-u.
- Kod klasičnog DH postoje napadi brži od isprobavanja, pa su potrebni veliki brojevi; za dobre krive takvi napadi nisu poznati.
- Standardne krive: P-256, P-384 (NIST SP 800-186), Curve25519 (RFC 7748). Kriva se ne pravi sama.
- Šorov algoritam razbija i ECC; kraći ključ ne znači veću otpornost na kvantne računare ([[Postkvantna kriptografija]]).

## Kako radi
Eliptička kriva je skup tačaka (x, y) koje zadovoljavaju `y² = x³ + ax + b`, sa koordinatama po modulu velikog prostog broja. Tačke se „sabiraju“: prava kroz dve tačke seče krivu u trećoj, čiji je odraz zbir. Množenje `k·G = G + G + … + G` računa se brzo, ponovljenim udvostručavanjem i sabiranjem, u nekoliko stotina koraka i za k od 256 bita. Obrnuto, naći k iz G i k·G praktično je nemoguće. To je osnova za X25519 ([[Diffie-Hellman razmena ključeva|razmena ključeva]]) i za potpise ECDSA i EdDSA.

## Potpisi na krivama
**ECDSA** je algoritam za [[Digitalni potpis|digitalni potpis]] nad eliptičkom krivom u kojem je potpis par brojeva (r, s): r je x koordinata tačke k·G za novu tajnu [[Jednokratna vrednost|jednokratnu vrednost]] k, a s = k⁻¹ · (h + r · d) mod n, gde je h [[Kriptografska heš funkcija|heš]] poruke, d privatni ključ, a n javni red tačke G (broj sabiranja posle kojeg se G vraća na početak). Ko zna k jednog potpisa, iz s izračuna d; isto važi i kada su dva potpisa napravljena sa istim k.

**EdDSA** (Ed25519, Ed448) je algoritam za potpis nad Edvardsovim oblikom krive u kojem se tajna vrednost potpisa ne bira slučajno, nego se izračunava kao heš dela privatnog ključa i same poruke. Vrednost je ista samo za istu poruku, a tada je isti i potpis, pa greška ponovljenog k ne može da nastane. Dobar dizajn uklanja mogućnost greške, umesto da je samo dokumentuje.

- Potpis na krivoj P-256 ili Ed25519 ima 64 bajta; RSA potpis iste jačine (3072 bita) ima 384.
- Naredba `ssh-keygen -t ed25519` pravi [[SSH]] par ključeva sa javnim ključem od 32 bajta; programer nigde ne bira tajnu vrednost potpisa, pa ne može ni da pogreši u njoj.
- NIST je Ed25519 i Ed448 2023. uvrstio u FIPS 186-5, uz ECDSA.

## Česti propusti i zaštita
- **Ponovljen k kod ECDSA.** Sony je potpisivao softver za PlayStation 3 ECDSA-om, ali sa istim k u svakom potpisu. Iz dva potpisa grupa fail0verflow je 2010. jednostavnom algebrom izračunala Sonyjev privatni ključ, pa je svako mogao da potpiše svoj program kao Sony. Isto se dešava kada [[Kriptografski generator slučajnih brojeva|generator]] ponavlja vrednosti. *Zaštita:* EdDSA, ili kod ECDSA deterministički k po RFC 6979.
- **Napad nevažećom krivom.** Server ne proverava da li primljena tačka leži na njegovoj krivoj. Napadač šalje tačke sa slabih krivih i iz odgovora deo po deo izvlači privatni ključ servera. Jager, Schwenk i Somorovsky (2015) su tako izvukli ključeve TLS servera zasnovanih na Bouncy Castle i Oracle Javi. *Zaštita:* provera tačke (obavezna za P-256) ili X25519, koji je projektovan tako da provera nije potrebna.
- **[[Napad merenjem vremena|Merenje vremena]].** Kod čije trajanje zavisi od bitova k otkriva ključ merenjem. *Zaštita:* biblioteke sa operacijama u konstantnom vremenu.
- **Konstante nepoznatog porekla.** Tačke na krivoj čije poreklo niko nije obrazložio mogu da sakriju zadnja vrata, kao u generatoru [[Kriptografski generator slučajnih brojeva#Česti propusti i zaštita|Dual_EC_DRBG]], gde je onaj ko zna tajnu vezu između dve konstantne tačke predviđao sve „slučajne“ brojeve. Slabija i nedokazana sumnja odnosi se na same NIST krive: koeficijenti P-256 i P-384 izvedeni su heširanjem semena čije poreklo nije objašnjeno. Slabost ovih krivih nije poznata i one su i danas preporučene, ali je ta sumnja jedan od razloga za krive kao Curve25519, čiji je svaki parametar obrazložen. *Zaštita:* krive i konstante sa javno obrazloženim izborom.
