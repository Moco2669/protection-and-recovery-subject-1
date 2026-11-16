---
tip: pojam
aliases: [log store, skladište logova]
izvor: nema posebne standardne definicije skladišta; srodno: NIST SP 800-92, "log", zapis o onome što se desilo u sistemima i mrežama organizacije
status: prihvaćeno
sloj: temelj
---
# Skladište zapisa (log store)

## Definicija
Zapis je unos o radnji koja se već desila u drugoj komponenti, sačuvan radi kasnijeg pregleda. Skladište zapisa je [[Skladište podataka|skladište podataka]] u kojem se čuvaju zapisi.

## Primer
[[Softverski proizvod|Softverski proizvod]] firme [[Fakturis]] ostavlja zapise u sopstvenom skladištu zapisa. Zapisi se čuvaju sedam dana.

Kontraprimer: tabela statusa faktura u [[Baza podataka|bazi podataka]] pokazuje trenutno stanje svake fakture, ali ne i ko ju je i kada menjao. Red fakture nije zapis. Tabela nije skladište zapisa.

## Napomene
- Zapise u ovo skladište upisuje [[Sistem za zapise o radu|sistem za zapise o radu]]. Definicija skladišta ne imenuje taj sistem, da dve definicije ne bi zavisile jedna od druge.

**Čuvanje na disku.** Zapisi se obično upisuju u tekstualne datoteke tako što se novi zapis samo dodaje na kraj. Zapisi stariji od zadatog roka se brišu.

**Pristup.** U firmi [[Fakturis]] skladište nije posebna usluga na mreži. Proces [[Softverski proizvod|proizvoda]] radi pod [[Servisni nalog|servisnim nalogom]] operativnog sistema i sme da dopisuje datoteku. Zaposleni je ne dopisuje. Datoteku čita administrator, nalogom tog servera i njegovom lozinkom. Kad bi skladište bilo izdvojena usluga, servis bi se predstavio pristupnim tokenom, a čovek svojim nalogom. Studija takvu uslugu ne koristi.

**Komande.** Upis novog zapisa i pretraga postojećih. Izmena ili brisanje pojedinačnog zapisa nije deo redovnog rada.
