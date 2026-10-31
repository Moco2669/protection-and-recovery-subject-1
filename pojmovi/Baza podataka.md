---
tip: pojam
aliases: [database, DBMS, sistem za upravljanje bazom podataka]
izvor: CIS Critical Security Controls v8, Glossary, "database"
status: predlog
sloj: temelj
---
# Baza podataka (database)

## Definicija
Baza podataka je softverska komponenta sistema koja trajno čuva strukturisane podatke i drugim komponentama omogućava da ih čitaju i menjaju preko upita, u granicama prava dodeljenih njihovim nalozima.

## Primer
[[Fakturis]] koristi PostgreSQL bazu na aplikacionom serveru. U njoj su nalozi korisnika sa hešovima lozinki, podaci o firmama korisnika, evidencije kupaca, fakture i statusi plaćanja. Jedina komponenta koja joj pristupa u radu je [[Web aplikacija|web aplikacija]]. Stefan joj pristupa radi održavanja, a [[Sistem za rezervne kopije|sistem za rezervne kopije]] svake noći pravi njenu kopiju.

Kontraprimer: Excel tabela u kojoj knjigovođa vodi mesečne prihode takođe sadrži strukturisane podatke, ali nema upite ni naloge. Ona je dokument u [[Skladište dokumenata|skladištu dokumenata]].

## Napomene
- CIS pod bazom podrazumeva samo podatke, a softver koji njima upravlja (DBMS) posmatra odvojeno. Ovde su obuhvaćeni zajedno, jer imaju iste ranjivosti i kontrole.
- U [[Fakturis]] se aplikacija na bazu povezuje kao njen vlasnik, pa njen nalog može i da briše tabele.
