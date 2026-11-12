---
tip: pojam
aliases: [relational database, RDBMS, SQL baza, PostgreSQL]
izvor: Codd, A Relational Model of Data for Large Shared Data Banks, Communications of the ACM 13(6), 1970; karakteristike prema PostgreSQL Documentation, Database File Layout i Routine Vacuuming
status: predlog
sloj: jezgro
---
# Relaciona baza podataka (relational database)

## Definicija
Relaciona baza podataka je [[Baza podataka|baza podataka]] koja podatke čuva kao redove tabela sa unapred zadatim kolonama, a veze između podataka izražava vrednostima u tim kolonama.

## Primer
[[Fakturis]] koristi PostgreSQL na aplikacionom [[Server|serveru]]. Tabele čuvaju korisnike, kupce, fakture i stavke faktura. Red u tabeli faktura upućuje na kupca preko kolone sa identifikatorom kupca.

Kontraprimer: [[Dokument-orijentisana baza podataka|dokument-orijentisana baza]] koja fakturu čuva kao jedan dokument sa ugnježdenom listom stavki nije relaciona. Ona ne traži unapred zadate kolone.

## Napomene
**Upotreba.** Najrasprostranjenija vrsta za poslovne podatke. Zadate kolone i veze između tabela drže povezane podatke, kao fakture, kupce i plaćanja, međusobno usklađenim, a SQL poznaje skoro svaki programer.

**Čuvanje na disku.** PostgreSQL čuva svaku tabelu i indeks u zasebnoj datoteci u direktorijumu podataka, a izmene najpre upisuje u transakcioni dnevnik (WAL). Obrisan ili izmenjen red ne nestaje odmah: stara verzija ostaje na disku dok je čišćenje (VACUUM) ne označi kao slobodan prostor. Ko čita direktorijum podataka ili kopiju baze, čita sve tabele, mimo prava u bazi.

**Pristup.** Baza prima veze na mrežnom portu, kod PostgreSQL-a podrazumevano 5432. Komponenta se prijavljuje nalogom baze, a prava se dodeljuju po tabelama, pa i po kolonama. [[Softverski proizvod|Proizvod]] pristupa bazi [[Servisni nalog|servisnim nalogom]].

**Komande.** Komponente šalju SQL kao tekst: SELECT za čitanje, INSERT, UPDATE i DELETE za izmenu, a nalozi sa većim pravima i naredbe koje menjaju strukturu ili prava, kao DROP i GRANT. Baza izvršava ceo tekst koji primi. Ako proizvod u tekst ugradi vrednost koju je uneo korisnik, korisnik može da promeni i sam [[Upitni jezik|upit]].
