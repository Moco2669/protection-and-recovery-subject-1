---
tip: pojam
aliases: [log store, skladište logova]
izvor: nema posebne standardne definicije skladišta; srodno: NIST SP 800-92, "log", zapis o onome što se desilo u sistemima i mrežama organizacije
status: prihvaćeno
sloj: temelj
---
# Skladište zapisa (log store)

## Definicija
Skladište zapisa je [[Skladište podataka|skladište podataka]] u kojem se čuvaju zapisi o radnjama u drugim komponentama, radi kasnijeg pregleda.

## Primer
[[Softverski proizvod|Softverski proizvod]] firme [[Fakturis]] ostavlja zapise u sopstvenom skladištu zapisa. Zapisi se čuvaju sedam dana.

Kontraprimer: tabela statusa faktura u [[Baza podataka|bazi podataka]] pokazuje trenutno stanje svake fakture, ali ne i ko ju je i kada menjao. Ona nije skladište zapisa.

## Napomene
- Zapise u ovo skladište upisuje [[Sistem za zapise o radu|sistem za zapise o radu]]. Definicija skladišta ne imenuje taj sistem, da dve definicije ne bi zavisile jedna od druge.
