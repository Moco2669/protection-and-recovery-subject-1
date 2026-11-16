---
tip: pojam
aliases: ["information disclosure"]
izvor: "Microsoft, Microsoft Threat Modeling Tool threats, STRIDE model, https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats; FTN, RBS 04 Modelovanje pretnji, slajdovi 48–60. Definicija je parafraza; manifestacije po komponentama su obrazložena primena, ne doslovan tekst izvora."
---

# Narušavanje poverljivosti podataka (information disclosure)

## Definicija

Narušavanje poverljivosti podataka je tip pretnje pri kojem napadač saznaje podatke ili ih učini dostupnim učesniku koji prema bezbednosnim zahtevima nema pravo da ih sazna.

## Primer

Poslovni dokument organizacije smeju da čitaju samo određeni korisnici. Ako napadač prati komunikacioni put i sazna sadržaj dokumenta koji se prenosi čitljivo, ostvaruje narušavanje poverljivosti tokom prenosa. Ranjivost je odsustvo potrebne zaštite na delu komunikacionog puta koji napadač može posmatrati. Primer ne tvrdi da postojeća studija slučaja već ima takvu vezu.

## Napomene

**Procesna jedinica.** Proizvod otkrije podatke kroz odgovor neovlašćenom primaocu, sadržaj greške ili podatke koje proces koristi tokom rada. Ranjivost može biti pogrešno ograničavanje izlaza ili prava pristupa.

**Tok podataka.** Napadač sazna sadržaj ili zaštićene podatke o komunikaciji tokom prenosa. Potrebno je navesti koje podatke sme da posmatra i šta zahtev nalaže da ostane poverljivo.

**Skladište podataka.** Napadač pročita podatke iz baze, datoteke, zapisa o radu, repozitorijuma ili sačuvane kopije kojima nema pravo pristupa. Repozitorijum može otkriti kod i tajne, a skladište zapisa podatke koje je proces prethodno zabeležio.

Narušavanje poverljivosti tokom prenosa i narušavanje poverljivosti sačuvanih podataka su manifestacije istog opštijeg tipa pretnje.

[[Narušavanje integriteta podataka]] odnosi se na nedozvoljenu izmenu, a ne na saznavanje sadržaja. Zaštita jedne veze ili skladišta ne dokazuje zaštitu drugih mesta na kojima se isti podaci pojavljuju.

