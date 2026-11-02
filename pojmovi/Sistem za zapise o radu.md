---
tip: pojam
aliases: [logging system, log management, sistem za logove]
izvor: NIST SP 800-92, Guide to Computer Security Log Management ("log": a record of the events occurring within an organization's systems and networks)
status: prihvaćeno
sloj: temelj
---
# Sistem za zapise o radu (logging system)

## Definicija
Sistem za zapise o radu je komponenta sistema koja prikuplja zapise o radnjama u drugim komponentama, čuva ih u [[Skladište zapisa|skladištu zapisa]] i omogućava njihov pregled.

## Primer
U firmi [[Fakturis]] sistem nije izdvojen. [[Softverski proizvod|Softverski proizvod]], programi na [[Server|serveru]] i [[Mrežni prolaz|mrežni prolaz]] upisuju zapise svaki u svoje skladište zapisa. Zapisi proizvoda čuvaju se sedam dana, a niko ih redovno ne pregleda.

Kontraprimer: tabela statusa faktura pokazuje trenutno stanje, ali je ne vodi ovaj sistem i ona ne služi pregledu toga ko je šta uradio.

## Napomene
- Zapisi o radu su istovremeno resurs: ko ih izmeni ili obriše, briše i trag ko je šta uradio.
