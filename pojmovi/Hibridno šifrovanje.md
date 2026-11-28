---
tip: pojam
aliases: [hybrid encryption, KEM/DEM]
izvor: 'IETF RFC 9180, Hybrid Public Key Encryption; NIST SP 800-227'
status: prihvaćeno
sloj: jezgro
---
# Hibridno šifrovanje (hybrid encryption)

## Definicija
Hibridno šifrovanje je šifrovanje podataka za vlasnika javnog ključa u kojem se podaci šifruju simetričnim algoritmom, po pravilu [[Autentifikovano šifrovanje|autentifikovanim]], novim ključem, a taj ključ se prenosi ili izvodi [[Asimetrična kriptografija|asimetričnim]] algoritmom, najčešće [[Mehanizam enkapsulacije ključa|KEM-om]].

## Primer
Firma šifruje noćne rezervne kopije baze, a [[Sistem za rezervne kopije|sistem za kopije]] ima samo javni ključ:

1. KEM-om ka javnom ključu dobija novu tajnu i njen šifrat.
2. Iz tajne izvodi AES-256 ključ i AES-GCM-om šifruje kopiju.
3. Upisuje šifrat tajne i šifrovanu kopiju, a tajnu i AES ključ briše iz memorije.

Privatni ključ je van mreže, kod dve osobe. Napadač koji preuzme sistem za kopije nema čime da pročita nijednu kopiju. Da je AES ključ bio u konfiguraciji tog sistema, krađa sistema bi značila krađu svih kopija.

## Napomene
- Asimetrično rešava raspodelu ključa, ali je sporo; simetrično je brzo, ali traži zajednički ključ. Hibrid uzima oba.
- HPKE (RFC 9180) standardizuje kombinaciju KEM + KDF + AEAD, npr. `DHKEM(X25519) + HKDF-SHA256 + AES-128-GCM`.
- Srodan obrazac u oblaku je šifrovanje omotačem (envelope encryption): podatke šifruje ključ podataka (DEK), a njega glavni ključ (KEK) koji ne napušta servis za ključeve. KEK je tu obično simetričan, pa to nije hibridno šifrovanje u užem smislu.
- Nije isto što i [[Hibridna razmena ključeva]], gde „hibridno“ znači klasično plus postkvantno.

## Česti propusti i zaštita
- **Privatni ključ na istom serveru kao šifrovani podaci.** Ko preuzme server, ima i podatke i ključ. *Zaštita:* privatni ključ odvojen, van mreže ili u hardverskom bezbednosnom modulu (HSM), iz kog ključ ne izlazi.
- **Jedan simetrični ključ za sve**, enkapsuliran jednom i korišćen godinama. *Zaštita:* nov ključ po fajlu ili poruci.
- **Dugoročni podaci sa klasičnim KEM-om** izloženi su napadu [[Prikupi sada dešifruj kasnije]]. *Zaštita:* hibridni klasično-postkvantni KEM.
