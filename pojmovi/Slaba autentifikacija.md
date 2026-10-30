| **tip** | pojam |
|---|---|
| **aliases** | weak authentication |
| **izvor** | [MITRE CWE-1390 — Weak Authentication](https://cwe.mitre.org/data/definitions/1390.html) |

# Slaba autentifikacija (weak authentication)

## Definicija

Slaba autentifikacija jeste slabost komponente sistema koja koristi mehanizam za proveru identiteta, ali njime nedovoljno pouzdano potvrđuje da je korisnik ili program zaista onaj za koga se predstavlja.

## Primer

U posmatranom sistemu firme, zaposleni može da obnovi pristup nalogu tako što unese svoju službenu e-mail adresu i odgovori na pitanje o datumu rođenja. Aplikacija zatim dozvoljava postavljanje nove lozinke, bez dodatne provere identiteta.

Napadač zna e-mail adresu zaposlenog, ali nema pristup njegovom e-mail sandučetu. Datum rođenja sazna sa javnog profila zaposlenog. Unošenjem ta dva podatka postavi novu lozinku i preuzme nalog u poslovnoj aplikaciji.

Mehanizam oporavka pristupa predstavlja konkretnu ranjivost jer podatke koje mogu znati i druge osobe prihvata kao dovoljan dokaz identiteta zaposlenog.

## Kontraprimer

Napadač zna istu e-mail adresu i datum rođenja zaposlenog, ali aplikacija ne dozvoljava promenu lozinke samo na osnovu tih podataka. Na prethodno potvrđenu e-mail adresu zaposlenog šalje nepredvidiv, vremenski ograničen kod koji se može upotrebiti samo jednom.

Kod stiže u e-mail sanduče zaposlenog. Pošto napadač nema pristup tom sandučetu, ne može da pročita kod i završi promenu lozinke. Samo poznavanje e-mail adrese ne omogućava čitanje poruka poslatih na nju.

## Napomene

Provera identiteta važna je i tokom prijave i tokom obnove pristupa nalogu. Ako se pouzdana prijava može zaobići slabijim postupkom promene lozinke, nalog ostaje izložen preuzimanju.

Slaba autentifikacija odnosi se na nedovoljno pouzdanu proveru identiteta. Neispravna kontrola pristupa odnosi se na omogućavanje radnje za koju korisnik ili program nije ovlašćen.
