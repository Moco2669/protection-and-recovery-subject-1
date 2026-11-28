---
tip: pojam
aliases: [message authentication code, MAC, HMAC, keyed-hash message authentication code, oznaka autentičnosti, tag, napad produženjem poruke, napad proširenjem dužine, length extension attack]
izvor: 'NIST CSRC Glossary, message authentication code; IETF RFC 2104, HMAC (https://www.rfc-editor.org/rfc/rfc2104.html)'
status: prihvaćeno
sloj: jezgro
---
# Kod za autentifikaciju poruke (message authentication code, MAC)

## Definicija
Kod za autentifikaciju poruke (MAC) je vrednost (oznaka) izračunata iz poruke i tajnog ključa, takva da bez tog ključa nije praktično moguće izračunati ispravnu oznaku ni za jednu poruku. Ko ima ključ, ponovnim izračunavanjem proverava da poruka nije menjana i da potiče od nekoga ko zna ključ.

## Primer
[[Spoljni servis]] za plaćanje šalje aplikaciji obaveštenje „porudžbina 142 plaćena“ na javnu adresu `/api/placanje`. Bez provere, svako može da pošalje takav zahtev i dobije robu bez plaćanja. Zato servis uz obaveštenje šalje HMAC oznaku, ključem koji deli samo sa aplikacijom:

```python
ocekivano = hmac.new(kljuc, vreme + "." + telo, hashlib.sha256).hexdigest()
if not hmac.compare_digest(ocekivano, oznaka):   # poređenje u konstantnom vremenu
    odbij()
if abs(sada - int(vreme)) > 300:                  # staro obaveštenje: moguće ponavljanje
    odbij()
```

## Napomene
- MAC štiti integritet i poreklo između strana koje dele ključ, ne poverljivost.
- MAC ne daje neporecivost: i primalac ima ključ, pa i on može da napravi oznaku. Za to služi [[Digitalni potpis]].
- **HMAC** je MAC napravljen od [[Kriptografska heš funkcija|heš funkcije]]: `H((K ⊕ opad) || H((K ⊕ ipad) || m))` (RFC 2104). `K` je ključ dopunjen nulama do veličine bloka heš funkcije; duži ključ se prvo hešira. `opad` i `ipad` su dve različite javne konstante. Drugi česti MAC-ovi su oznake u [[Autentifikovano šifrovanje|AEAD-u]] (GCM, Poly1305).
- Za razliku od heša, koji svako može da izračuna, HMAC oznaku može da napravi samo onaj ko zna ključ.
- HMAC se koristi i za oznaku JWT tokena (HS256; JWT je naziva potpisom, ali je to MAC) i zahteva ka [[Objektno skladište|objektnom skladištu]] (AWS Signature V4).

## Napad produženjem poruke
Heš funkcije MD5, SHA-1, SHA-256 i SHA-512 obrađuju poruku blok po blok, a izlaz je celo unutrašnje stanje posle poslednjeg bloka. Ko zna `H(K || m)` i dužinu `K || m`, postavi to stanje kao početno i nastavi heširanje: dobija ispravan heš za `K || m || dopuna || dodatak`, bez ključa. Bajtovi dopune ostaju u sredini poruke, ali za mnoge formate to ne smeta (npr. parametar `&admin=1` dodat na kraj zahteva).

| Podležu | Ne podležu |
| --- | --- |
| MD5, SHA-1, SHA-256, SHA-512 | SHA-3: deo stanja se nikad ne objavljuje |
| SHA-224: skriva samo 32 bita stanja, koja se mogu pogoditi | SHA-384, SHA-512/256: izlaz je skraćen, skriveno je 128 i više bita stanja |
| | BLAKE2 |

HMAC sprečava ovaj napad za svaku heš funkciju. Unutrašnji heš bi se mogao proširiti, ali napadač ga nikad ne vidi. Spoljašnji vidi, ali njegov nastavak nije HMAC nijedne poruke, jer onaj ko proverava spolja uvek hešira tačno blok ključa i unutrašnji heš fiksne dužine. HMAC se ne oslanja ni na otpornost heša na kolizije, pa za HMAC-MD5 nije poznat praktičan napad (RFC 6151). Ipak se u novim sistemima koristi HMAC-SHA256.

## Česti propusti i zaštita
- **Oznaka se ne proverava**, samo se gleda da zaglavlje postoji. *Zaštita:* uvek izračunati i uporediti (CWE-347).
- **Obično poređenje stringova** prekida na prvom različitom bajtu; merenjem vremena napadač pogađa oznaku bajt po bajt ([[Napad merenjem vremena]]). *Zaštita:* `hmac.compare_digest` ili ekvivalent.
- **Ponavljanje.** Napadač snimi ispravno obaveštenje i pošalje ga ponovo. *Zaštita:* vreme ili jedinstveni identifikator u delu nad kojim se računa oznaka, i pamćenje obrađenih.
- **`H(ključ || poruka)` umesto HMAC-a.** Flickr API (2009) je zahteve štitio kao `MD5(tajna || parametri)`; Duong i Rizzo su napadom produženjem poruke pravili ispravno označene zahteve u ime bilo koje aplikacije. *Zaštita:* HMAC.
- **JWT sa slabim ključem ili izborom algoritma u tokenu.** Token zaštićen HS256 ključem `secret` probija se offline iz jednog tokena, posle čega napadač pravi tokene za bilo kog korisnika. Ako biblioteka veruje polju `alg` iz tokena, napadač pošalje `none` ili token „potpiše“ HS256 algoritmom koristeći javni RSA ključ servera kao HMAC ključ. *Zaštita:* slučajan ključ od bar 256 bita i algoritam fiksiran na serveru.
