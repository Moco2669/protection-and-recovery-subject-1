---
tip: pojam
aliases: [software product, web aplikacija, web application]
izvor: ISO/IEC/IEEE 12207:2008, tačka 4.42 (ista rečenica u izdanju 2026, tačka 3.1.54)
status: prihvaćeno
sloj: temelj
---
# Softverski proizvod (software product)

## Definicija
Softverski proizvod je skup softverskih komponenti koje organizacija sama razvija i izvršava, i preko kojih korisnici ili drugi programi koriste njene poslovne funkcije.

## Primer
Proizvod firme [[Fakturis]] izvršava se na aplikacionom [[Server|serveru]]. Korisnici preko njega izdaju fakture. Proizvod čita i menja podatke u [[Baza podataka|bazi podataka]], upisuje fakture u [[Skladište datoteka|skladište datoteka]] i preko [[Interfejs ka spoljnom servisu|interfejsa ka spoljnom servisu]] poziva [[Spoljni servis|spoljni servis]] za naplatu.

Kontraprimer: program na istom serveru koji samo prosleđuje saobraćaj proizvodu nije softverski proizvod. Firma ga nije razvila, i on ne obavlja poslovne funkcije.

## Napomene
- Definicija ne fiksira da li je proizvod jedan program ili više delova, ni kojim protokolom govori.
- „Poslovne funkcije“ nisu poseban pojam u bazi. Stoje u običnom značenju.
- Mera problema i dalje govori o malicioznim zahtevima. Definicija ne traži da proizvod prima zahteve. Ako protokol kasnije nije zahtev i odgovor, menja se mera.
