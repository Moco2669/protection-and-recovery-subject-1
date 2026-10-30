---
tip: pojam
aliases: [server, host, aplikacioni server]
izvor: CIS Critical Security Controls v8, Glossary, "servers"
status: predlog
sloj: temelj
---
# Server (server)

## Definicija
Server je računar, fizički ili virtuelni, zajedno sa operativnim sistemom, na kom se izvršavaju programi koji drugim [[Komponenta sistema|komponentama sistema]] pružaju usluge ili podatke preko mreže.

## Primer
Glavni server firme [[Fakturis]] je aplikacioni server u server sobi: fizička mašina sa Ubuntu Server operativnim sistemom i nginx web serverom, na kojoj se izvršava [[Web aplikacija|web aplikacija]]. Firma ima još tri servera: NAS [[Skladište dokumenata|skladišta dokumenata]], GitLab server sa [[Repozitorijum izvornog koda|repozitorijumom]] i server [[Sistem za rezervne kopije|za rezervne kopije]].

Kontraprimer: Jelenin laptop izvršava programe samo za nju i ne pruža usluge drugim komponentama, pa je [[Poslovni računar|poslovni računar]], a ne server.

## Napomene
- Server i programi koji se na njemu izvršavaju su različite komponente. Ako napadač preuzme operativni sistem aplikacionog servera, dobija pristup i aplikaciji, i njenim zapisima o radu, i podešavanjima sa lozinkom baze.
- U [[Fakturis]] Ubuntu i nginx na aplikacionom serveru nisu ažurirani od marta.
