| **tip** | pojam |
|---|---|
| **aliases** | insufficient logging and monitoring |
| **izvor** | [OWASP Top 10:2025 — A09 Security Logging and Alerting Failures](https://top10.owasp.org/2025/A09_2025-Security_Logging_and_Alerting_Failures/) |

# Nedovoljno beleženje i praćenje (insufficient logging and monitoring)

## Definicija

Nedovoljno beleženje i praćenje jeste slabost u kojoj sistem ne čuva potrebne podatke o bezbednosno značajnim događajima ili ih ne prati i ne analizira dovoljno da bi se sumnjive aktivnosti pravovremeno uočile i istražile.

## Primer

Aplikacija firme ne beleži neuspešne pokušaje prijave. Napadač tokom noći isprobava veliki broj lozinki za nalog zaposlenog, ali ne postoji zapis ni upozorenje o tim pokušajima.

Administrator zato ne dobija signal za proveru. Ako nalog kasnije bude preuzet, nedostaju i podaci za istraživanje prethodnih pokušaja. Ova slabost otežava otkrivanje i razjašnjavanje napada.

## Kontraprimer

Aplikacija beleži neuspešne prijave sa vremenom, nalogom i izvorom zahteva. Sistem prati ponavljanja i pri neuobičajenom broju pokušaja šalje upozorenje nadležnom administratoru, koji ga proverava.

Opisani pokušaji ostavljaju trag i pokreću proveru. Samo upozorenje, međutim, ne blokira automatski prijavu.

## Napomene

Beleženje stvara zapise, odnosno logove. Praćenje koristi te zapise i druge pokazatelje za prepoznavanje sumnjivih aktivnosti.

Ova slabost ne mora omogućiti početni ulazak napadača, ali može produžiti vreme u kojem napad ostaje neprimećen.

U zapise ne treba upisivati lozinke, tajne ključeve ili jednokratne kodove. Važni su i zaštita zapisa od izmene i kontrolisan pristup njima.
