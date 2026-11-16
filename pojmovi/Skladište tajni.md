---
tip: pojam
aliases: [secrets store, secrets manager, upravljanje tajnama, vault]
izvor: OWASP Secrets Management Cheat Sheet
status: predlog
sloj: jezgro
---
# Skladište tajni (secrets store)

## Definicija
Skladište tajni je [[Skladište podataka|skladište podataka]] u kojem se vrednost traži po nazivu, kao u [[Ključ-vrednost baza podataka|ključ-vrednost bazi]]. Namenjeno je tajnama, vrednostima kojima jedna komponenta dokazuje pravo pristupa drugoj, kao što su lozinka naloga u bazi, API ključ i kriptografski ključ. Svaku tajnu izdaje pojedinačno, samo komponenti koja na nju ima pravo.

## Primer
API ključ [[Spoljni servis|spoljnog servisa]] za naplatu firma [[Fakturis]] čuva kao deo podešavanja. Ako su podešavanja u [[Repozitorijum izvornog koda|repozitorijumu izvornog koda]], ključ vidi svaki programer i on ostaje u istoriji izmena. Sa skladištem tajni u repozitorijumu stoji samo naziv tajne, a [[Softverski proizvod|proizvod]] pri pokretanju traži njenu vrednost od skladišta. Programeri tu vrednost ne dobijaju.

Kontraprimer: datoteka sa podešavanjima na aplikacionom [[Server|serveru]] može da sadrži iste tajne, ali server ne zna koja je vrednost u njoj tajna. Ko sme da čita datoteku, čita sve tajne u njoj odjednom.

## Napomene
**Upotreba.** Koristi se kada više komponenti koristi lozinke i ključeve. Tajne su na jednom mestu, sa pravilima i beleženjem, umesto rasute po kodu i podešavanjima.

**Čuvanje na disku.** Tajne su na disku šifrovane, a ključ za njihovo dešifrovanje drži se odvojeno od njih. Kopija diska skladišta zato ne otkriva tajne sama po sebi.

**Pristup.** Za svaku tajnu posebno se određuje koja komponenta sme da je čita, a svako čitanje se beleži. Servis se predstavlja pristupnim tokenom ili [[Servisni nalog|servisnim nalogom]]. Čovek, ako sme da čita tajnu, ima drugi nalog. Token nosi spisak tajni koje sme da pročita, ne pravo nad celim skladištem. Ko preuzme taj token, dobija te tajne.

**Razlika od ključ-vrednost skladišta.** I ovde se vrednost traži po nazivu. [[Ključ-vrednost baza podataka|Ključ-vrednost baza]], na primer Redis, drži vrednost čitljivu u memoriji. Prijavu čini jedna lozinka ili nalog sa spiskom naredbi. Čitanje se ne beleži po vrednosti. Nalog koji sme sve naredbe može da pročita sve i da promeni podešavanja. Skladište tajni na disku drži vrednosti šifrovane, a ključ za dešifrovanje odvojeno od njih. Kopija diska Redisa zato otkriva vrednosti. Kopija diska ovog skladišta ne otkriva ih sama. Zbog istog oblika ovo nije peta podvrsta [[Skladište podataka|skladišta podataka]]. Posebne su zaštite.

**Komande.** Programski interfejs sa naredbama za čitanje tajne po nazivu, upis nove vrednosti i zamenu postojeće. Vrednost se vraća čitljiva, pa je vidi i svaki program koji radi pod istim nalogom kao komponenta kojoj je izdata.

Tajna upisana u izvorni kod ostaje u istoriji repozitorijuma i kada se obriše iz poslednje verzije. Treba je zameniti, a ne samo ukloniti.

Primer je ilustrativan. Studija ne određuje da Fakturis ima skladište tajni.
