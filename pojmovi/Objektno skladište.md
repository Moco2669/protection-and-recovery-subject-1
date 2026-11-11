---
tip: pojam
aliases: [object storage, object store, S3, bucket, kontejner]
izvor: nema posebne standardne definicije; karakteristike prema AWS, Amazon S3 User Guide, What is Amazon S3?
status: predlog
sloj: jezgro
---
# Objektno skladište (object storage)

## Definicija
Objektno skladište je [[Skladište datoteka|skladište datoteka]] koje svaku datoteku čuva kao objekat, sadržaj sa opisnim podacima, pod jedinstvenim ključem u kontejneru (bucket), a pristup objektima daje preko programskog interfejsa zasnovanog na HTTP-u.

## Primer
Kada bi [[Fakturis]] PDF fakture čuvao u objektnom skladištu u oblaku umesto na mrežnom uređaju, svaka faktura bila bi objekat sa ključem poput `fakture/2026/0142.pdf` u kontejneru firme. [[Softverski proizvod|Proizvod]] bi je upisivao i čitao HTTP zahtevima potpisanim pristupnim ključem.

Kontraprimer: [[Deljeni mrežni folder|deljeni mrežni folder]] čuva iste datoteke, ali ih zaposleni otvaraju kao disk i kreću se kroz foldere. U uobičajenom kontejneru objektnog skladišta foldera nema: kosa crta u ključu je samo deo naziva.

## Napomene
**Upotreba.** Koristi se kada aplikacija čuva mnogo datoteka i skladište treba da raste bez planiranja kapaciteta: otpremljeni dokumenti, rezervne kopije i sadržaj sajta.

**Čuvanje na disku.** Organizacija datoteka na diskovima nije vidljiva od strane korisnika. Skladište može da čuva i prethodne verzije objekta, pa obrisan ili prepisan objekat ostaje dostupan. Može i da zabrani brisanje i izmenu objekta na zadato vreme.

**Pristup.** Svaki zahtev je ili potpisan pristupnim ključem ili anoniman. Ko sme šta, određuju politike kontejnera i naloga. Kontejneri i objekti su podrazumevano privatni, ali se mogu učiniti javnim, i tada ih svako otvara iz pregledača.

**Komande.** HTTP zahtevi nad objektima: PUT za upis, GET za čitanje, DELETE za brisanje i zahtev za spisak ključeva u kontejneru.

Razlika prema [[Deljeni mrežni folder|deljenom mrežnom folderu]] nije u tome gde se skladište nalazi. Objektno skladište može da radi i u prostorijama firme, na primer MinIO, a deljeni folder može biti usluga u oblaku. Razlika je u obliku podataka i načinu pristupa: objekat pod ključem, kome se pristupa HTTP zahtevima i koji se po pravilu upisuje ceo, nasuprot datoteci u stablu foldera, koja se otvara kao na disku i menja na mestu.

Primer je ilustrativan. Fakturis u studiji ne koristi objektno skladište.
