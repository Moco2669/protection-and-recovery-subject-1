---
tip: pojam
aliases: [logging system, log management, sistem za logove]
izvor: NIST SP 800-92, Guide to Computer Security Log Management ("log": a record of the events occurring within an organization's systems and networks)
status: predlog
sloj: temelj
---
# Sistem za zapise o radu (logging system)

## Definicija
Sistem za zapise o radu je [[Komponenta sistema|komponenta sistema]] koja prikuplja zapise o radnjama i događajima u drugim komponentama, čuva ih i omogućava njihov pregled.

## Primer
U firmi [[Fakturis]] ovaj sistem još nije izdvojen. [[Web aplikacija]], nginx na [[Server|serveru]] i [[Mrežni prolaz|mrežni prolaz]] vode zapise svako na svom uređaju. Zapisi aplikacije čuvaju se sedam dana, a niko ih redovno ne pregleda. Logička komponenta ipak postoji: to je skup tih zapisa i načina na koji se čuvaju.

Kontraprimer: tabela statusa faktura u bazi pokazuje trenutno stanje svake fakture, ali ne i ko ju je i kada menjao. Ona nije zapis o radu.

## Napomene
- Zapisi o radu su istovremeno [[Resurs|resurs]] (prateći) i preduslov za [[Detektivna kontrola|detektivne kontrole]] i za [[Neporecivost|neporecivost]]. Napadač koji ih izmeni ili obriše briše i tragove napada.
- Karakteristična ranjivost: [[Nedovoljno beleženje i praćenje]].
