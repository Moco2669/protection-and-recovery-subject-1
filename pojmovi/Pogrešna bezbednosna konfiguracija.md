---
tip: pojam
aliases: ["security misconfiguration"]
izvor: "OWASP Top 10:2025 — A02 Security Misconfiguration, https://top10.owasp.org/2025/A02_2025-Security_Misconfiguration/"
---

# Pogrešna bezbednosna konfiguracija (security misconfiguration)

## Definicija

Pogrešna bezbednosna konfiguracija jeste [[Slabost|slabost]] nastala zbog podešavanja komponente sistema koja nisu usklađena sa njenim bezbednosnim zahtevima.

## Primer

Firma čuva ugovore u folderu na serveru. Ugovore smeju da čitaju samo zaposleni iz računovodstva. Prilikom podešavanja deljenja foldera administrator izabere „Svi korisnici“, umesto „Računovodstvo“.

Zaposleni iz drugog odeljenja sada može da otvori ugovore koje ne sme da vidi. Program za deljenje fajlova radi kako je podešen, ali je izabrano pogrešno podešavanje. Time je omogućeno narušavanje poverljivosti ugovora.

## Napomene

Konfiguracija znači skup podešavanja: ko može da pristupi folderu, koji servisi su uključeni ili koje informacije server prikazuje.

Problem ne mora biti greška u programskom kodu. Može nastati izborom neodgovarajuće opcije ili zadržavanjem nebezbednih fabričkih podešavanja.

U primeru, pogrešna konfiguracija opisuje uzrok, a neispravna kontrola pristupa njegovu posledicu. Ove vrste slabosti mogu se preklapati.
