---
tip: pojam
aliases: [logging system, log management, sistem za logove]
izvor: NIST SP 800-92, Guide to Computer Security Log Management ("log": a record of the events occurring within an organization's systems and networks)
status: predlog
sloj: temelj
---
# Sistem za zapise o radu (logging system)

## Definicija
Sistem za zapise o radu je komponenta sistema koja prikuplja zapise o radnjama i događajima u drugim komponentama, čuva ih i omogućava njihov pregled.

## Primer
U firmi [[Fakturis]] ovaj sistem još nije izdvojen. [[Web aplikacija]], nginx na [[Server|serveru]] i [[Mrežni prolaz|mrežni prolaz]] vode zapise svako na svom uređaju. Zapisi aplikacije čuvaju se sedam dana, a niko ih redovno ne pregleda.

Kontraprimer: tabela statusa faktura u bazi pokazuje trenutno stanje svake fakture, ali ne i ko ju je i kada menjao. Ona nije zapis o radu.

## Napomene
- Zapisi o radu su istovremeno resurs, prateći: ko ih izmeni ili obriše, briše i trag ko je šta uradio.
- U [[Fakturis]] aplikacija beleži samo greške, ne i prijave, storniranja i promene statusa, a zapise niko redovno ne pregleda.
