---
tip: pojam
aliases: [Control-Flow Integrity, CFI]
izvor: 'Abadi et al., Control-Flow Integrity: Principles, Implementations, and Applications, ACM CCS 2005: https://www.cs.columbia.edu/~suman/secure_sw_devel/p340-abadi.pdf; Microsoft Learn, Control Flow Guard: https://learn.microsoft.com/en-us/windows/win32/secbp/control-flow-guard; LLVM/Clang, Control Flow Integrity: https://clang.llvm.org/docs/ControlFlowIntegrity.html'
status: prihvaćeno
---
# Integritet toka izvršavanja (Control-Flow Integrity)

## Definicija
Integritet toka izvršavanja je [[Tehnička kontrola]] koja ograničava putanje izvršavanja programa na one dozvoljene unapred utvrđenom bezbednosnom politikom i proverava da prenosi kontrole čije se odredište određuje tokom izvršavanja vode samo na dozvoljena odredišta.

## Primer
Modul za generisanje PDF faktura u [[Fakturis]] koristi pokazivač na funkciju kao povratni poziv za obradu naziva kupca. Bezbednosna politika CFI dozvoljava da se sa tog mesta pozove samo funkcija koja bezbedno priprema tekst za upis u PDF dokument.

Napadač iskorišćava [[Prekoračenje bafera]] da promeni vrednost pokazivača na funkciju i postavi adresu druge, nedozvoljene funkcije. Kada modul pokuša da pozove funkciju preko izmenjenog pokazivača, CFI provera utvrđuje da cilj nije dozvoljen i prekida izvršavanje programa.

## Napomene
- CFI je [[Preventivna kontrola|preventivna]] jer sprečava izvršavanje prenosa kontrole koji nisu dozvoljeni utvrđenom politikom. Ne uklanja memorijsku ranjivost koja je omogućila izmenu pokazivača ili drugog upravljačkog podatka.
- U opštem modelu CFI dozvoljene putanje predstavljaju se grafom toka izvršavanja programa. Provera tokom izvršavanja obezbeđuje da se stvarni prenosi kontrole uklapaju u taj graf.
- Razlikuju se **forward-edge** prenosi kontrole, kao što su indirektni pozivi funkcija i skokovi, i **backward-edge** prenosi, kao što su povratci iz funkcija. Konkretna implementacija ne mora da štiti obe vrste.
- Microsoft Control Flow Guard (CFG) je konkretna Microsoftova implementacija CFI-ja koja proverava ciljeve indirektnih poziva. Ne treba je poistovećivati sa opštim pojmom CFI. LLVM/Clang pruža više CFI provera, uključujući indirektne pozive i virtuelne pozive.
- CFI može da oteža [[Ponovna upotreba koda|ponovnu upotrebu koda]] ako napad zahteva nedozvoljene prenose kontrole. Međutim, zaštita od ROP-a zavisi od toga da li implementacija obuhvata i backward-edge, odnosno povratke iz funkcija. CFI koji proverava samo indirektne pozive ne mora da zaustavi ROP lanac zasnovan na povratnim adresama.
- CFI ne sprečava napade koji menjaju podatke bez nedozvoljenog prenosa kontrole. Takođe ne garantuje bezbednost ako napadač uspe da ostane unutar dozvoljenih putanja izvršavanja.
- U primeru za [[Fakturis]] pretpostavlja se da modul koristi pokazivač na funkciju kao povratni poziv i da je poziv obuhvaćen CFI proverom čija politika isključuje napadačev cilj. To nije utvrđena implementacija proizvoda.
