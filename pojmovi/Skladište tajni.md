---
tip: pojam
aliases: [secrets store, secrets manager, upravljanje tajnama, vault]
izvor: OWASP Secrets Management Cheat Sheet
status: predlog
sloj: jezgro
---
# Skladište tajni (secrets store)

## Definicija
Skladište tajni je [[Skladište podataka|skladište podataka]] namenjeno tajnama, odnosno vrednostima kojima jedna komponenta dokazuje pravo pristupa drugoj, kao što su lozinka naloga u bazi, API ključ i kriptografski ključ. Svaku tajnu izdaje pojedinačno, samo komponenti koja na nju ima pravo.

## Primer
API ključ [[Spoljni servis|spoljnog servisa]] za naplatu firma [[Fakturis]] čuva kao deo podešavanja. Ako su podešavanja u [[Repozitorijum izvornog koda|repozitorijumu izvornog koda]], ključ vidi svaki programer i on ostaje u istoriji izmena. Sa skladištem tajni u repozitorijumu stoji samo naziv tajne, a [[Softverski proizvod|proizvod]] pri pokretanju traži njenu vrednost od skladišta. Programeri tu vrednost ne dobijaju.

Kontraprimer: datoteka sa podešavanjima na aplikacionom [[Server|serveru]] može da sadrži iste tajne, ali server ne zna koja je vrednost u njoj tajna. Ko sme da čita datoteku, čita sve tajne u njoj odjednom.

## Napomene
**Upotreba.** Koristi se kada više komponenti koristi lozinke i ključeve. Tajne su na jednom mestu, sa pravilima i beleženjem, umesto rasute po kodu i podešavanjima.

**Čuvanje na disku.** Tajne su na disku šifrovane, a ključ za njihovo dešifrovanje drži se odvojeno od njih. Kopija diska skladišta zato ne otkriva tajne sama po sebi.

**Pristup.** Za svaku tajnu posebno se određuje koja komponenta sme da je čita, a svako čitanje se beleži. Komponenta se skladištu predstavlja sopstvenim pristupnim tokenom ili [[Servisni nalog|servisnim nalogom]]. Ko preuzme taj token, dobija sve tajne koje token sme da čita.

**Komande.** Programski interfejs sa naredbama za čitanje tajne po nazivu, upis nove vrednosti i zamenu postojeće. Vrednost se vraća čitljiva, pa je vidi i svaki program koji radi pod istim nalogom kao komponenta kojoj je izdata.

Tajna upisana u izvorni kod ostaje u istoriji repozitorijuma i kada se obriše iz poslednje verzije. Treba je zameniti, a ne samo ukloniti.

Primer je ilustrativan. Studija ne određuje da Fakturis ima skladište tajni.
