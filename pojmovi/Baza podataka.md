---
tip: pojam
aliases: [database, DBMS, sistem za upravljanje bazom podataka, SQL baza, relaciona baza]
izvor: CIS Critical Security Controls v8, Glossary, "database"
status: prihvaćeno
sloj: temelj
---
# Baza podataka (database)

## Definicija
Baza podataka je [[Skladište podataka|skladište podataka]] koje čuva strukturisane podatke i drugim komponentama omogućava da ih čitaju i menjaju preko upita, u granicama prava dodeljenih njihovim nalozima.

## Primer
[[Fakturis]] koristi PostgreSQL bazu na aplikacionom serveru. U njoj su nalozi korisnika, podaci o firmama, kupci, fakture i statusi plaćanja. U radu joj pristupa [[Softverski proizvod|softverski proizvod]]. Stefan joj pristupa radi održavanja, a [[Sistem za rezervne kopije|sistem za rezervne kopije]] pravi njenu kopiju.

Kontraprimer: Excel tabela u kojoj knjigovođa vodi mesečne prihode takođe sadrži strukturisane podatke, ali nema upite ni naloge. Ona je datoteka u [[Skladište datoteka|skladištu datoteka]].

## Napomene
- CIS pod bazom podrazumeva samo podatke, a softver koji njima upravlja posmatra odvojeno. Ovde su obuhvaćeni zajedno, jer imaju iste ranjivosti i kontrole.
- SQL je jezik upita u primeru, ne uslov definicije. Alias „SQL baza“ pokriva naziv podvrste sa časa.
