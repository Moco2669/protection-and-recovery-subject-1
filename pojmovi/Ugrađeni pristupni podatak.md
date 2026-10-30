| **tip** | pojam |
|---|---|
| **aliases** | hard-coded credential |
| **izvor** | [MITRE CWE-798 — Use of Hard-coded Credentials](https://cwe.mitre.org/data/definitions/798.html) |

# Ugrađeni pristupni podatak (hard-coded credential)

## Definicija

Ugrađeni pristupni podatak jeste slabost u kojoj je tajna za dokazivanje identiteta ili pristup servisu, poput lozinke ili API ključa, upisana neposredno u izvorni kod ili ugrađena u program.

## Primer

Aplikacija firme koristi API ključ za pristup spoljnom servisu za naplatu. Ključ je tajna kojom aplikacija dokazuje da sme da koristi servis. Programer ga upiše direktno u izvorni kod, dostupan svim programerima firme.

Zahtev firme predviđa da produkcionom ključu pristupaju samo aplikacija i ovlašćeni administrator. Osoba koja može da pročita kod sada može da kopira ključ i koristi servis u ime aplikacije, u granicama prava tog ključa.

## Kontraprimer

Kod sadrži samo oznaku tajne koju aplikacija učitava iz posebnog skladišta tajni. Sam ključ nije u kodu, a programer nema dozvolu da ga pročita iz skladišta. Kopiranje izvornog koda zato ne otkriva ključ.

## Napomene

Korisničko ime ili javna adresa servisa nisu automatski tajne. U ovom pojmu problem je ugrađivanje poverljive vrednosti koja omogućava pristup.

Ako je ključ već otkriven, brisanje iz poslednje verzije koda nije dovoljno. Može ostati u istoriji ili kopijama repozitorijuma; potrebno ga je opozvati ili zameniti.
