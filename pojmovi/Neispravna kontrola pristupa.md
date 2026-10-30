| **tip** | pojam |
|---|---|
| **aliases** | broken access control, improper access control |
| **izvor** | [OWASP Top 10:2025 — A01 Broken Access Control](https://top10.owasp.org/2025/A01_2025-Broken_Access_Control/); [MITRE CWE-862 — Missing Authorization](https://cwe.mitre.org/data/definitions/862.html) |

# Neispravna kontrola pristupa (broken access control)

## Definicija

Neispravna kontrola pristupa jeste slabost u sprovođenju pravila pristupa zbog koje komponenta sistema omogućava korisniku ili programu da pristupi resursu ili izvrši radnju za koju nije ovlašćen.

## Primer

U posmatranom sistemu firme, zaposleni iz korisničke podrške sme da pregleda fakture, dok storniranje faktura sme da izvršava samo računovodstvo. Aplikacija zaposlenom iz podrške ne prikazuje dugme za storniranje, ali serverski modul ne proverava njegovo pravo pri obradi zahteva.

Zaposleni neposredno pošalje zahtev za storniranje i aplikacija ga izvrši. Izostanak serverske provere predstavlja konkretnu ranjivost modula: omogućava nedozvoljenu izmenu fakture i narušava njen integritet.

## Kontraprimer

Zaposleni iz podrške neposredno pošalje zahtev za storniranje fakture, ali serverski modul proveri njegova prava i odbije zahtev. Za tu radnju kontrola pristupa je ispravno sprovedena, iako korisnik može da pošalje zahtev.

## Napomene

Autentifikacija proverava identitet korisnika, dok autorizacija proverava da li on ima pravo da izvrši određenu radnju nad određenim resursom. Uspešna prijava zato ne daje pravo na korišćenje svih funkcija aplikacije.

Neispravna kontrola pristupa obuhvata potpuno odsustvo potrebne provere, ali i proveru koja se izvršava pogrešno. Može omogućiti pristup tuđim podacima ili izvršavanje funkcija rezervisanih za drugu ulogu.

Sakrivanje dugmeta ili linka nije dovoljna zaštita. Pravo pristupa mora se proveravati na serverskoj strani, jer korisnik može neposredno poslati zahtev za podatak ili funkciju.
