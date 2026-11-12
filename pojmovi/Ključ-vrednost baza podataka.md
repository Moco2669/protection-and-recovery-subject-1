---
tip: pojam
aliases: [key-value store, key-value database, ključ-vrednost skladište, keš, Redis]
izvor: nema posebne standardne definicije; karakteristike prema Redis dokumentaciji, Redis security i Redis persistence
status: predlog
sloj: jezgro
---
# Ključ-vrednost baza podataka (key-value store)

## Definicija
Ključ-vrednost baza podataka je [[Baza podataka|baza podataka]] koja podatke programa čuva kao parove ključa i vrednosti i podatku pristupa po njegovom ključu. Vrednost je pojedinačan podatak, kao broj, tekst ili lista, a ne datoteka.

## Primer
Kada bi [[Softverski proizvod|softverski proizvod]] firme [[Fakturis]] sesije prijavljenih korisnika čuvao u Redis-u, ključ bi bio identifikator sesije iz kolačića pregledača, a vrednost podaci o prijavljenom korisniku. Pri svakom zahtevu proizvod bi čitao vrednost po ključu iz kolačića.

Kontraprimer: tabela sesija u [[Relaciona baza podataka|relacionoj bazi]] čuva iste podatke, ali joj se pristupa SQL upitom koji može da traži po bilo kojoj koloni.

## Napomene
**Upotreba.** Koristi se kada je potreban vrlo brz pristup podatku po poznatom ključu: sesije prijavljenih korisnika, keš i brojači, na primer pokušaja prijave. Brzina dolazi od toga što su podaci u radnoj memoriji.

**Čuvanje na disku.** Redis drži podatke u radnoj memoriji. Na disk ih upisuje kao povremeni snimak celog skupa (RDB, datoteka `dump.rdb`), kao dnevnik svih naredbi upisa (AOF), ili nikako kada služi samo kao keš. Snimak je jedna datoteka sa svim podacima.

**Pristup.** Redis je projektovan za pouzdane klijente u pouzdanom okruženju i ne treba da bude dostupan sa interneta. Podrazumevani port je 6379. Stariji način prijave je jedna lozinka zajednička svim klijentima, upisana čitljivo u datoteku podešavanja. Noviji su nalozi sa listama dozvoljenih naredbi (ACL). Bez lozinke i uz podrazumevana podešavanja Redis odgovara samo klijentima sa istog računara.

**Komande.** Kratke naredbe, kao GET i SET, ali i administrativne: FLUSHALL briše sve podatke, a CONFIG menja podešavanja i omogućava upis datoteke na proizvoljnu putanju servera. Klijent sa punim pristupom može da koristi sve naredbe.

[[Objektno skladište|Objektnom skladištu]] se takođe pristupa po ključu. Razlika je u tome šta je vrednost: tamo je to datoteka sa opisnim podacima, čiji sadržaj skladište ne tumači i kojoj se pristupa HTTP zahtevima, a ovde pojedinačan podatak programa, često u radnoj memoriji, kome se pristupa kratkim naredbama. Redis zna i tip vrednosti, pa brojač ili listu menja na mestu.

Primer je ilustrativan. Studija ne određuje gde Fakturis čuva sesije.
