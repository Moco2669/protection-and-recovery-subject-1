---
tip: pojam
aliases: [double free, double-free]
izvor: 'MITRE CWE-415, Double Free: https://cwe.mitre.org/data/definitions/415.html; MITRE CWE-672, Operation on a Resource after Expiration or Release: https://cwe.mitre.org/data/definitions/672.html'
status: prihvaćeno
sloj: jezgro
---
# Dvostruko oslobađanje (double free)

## Definicija
Dvostruko oslobađanje je [[Vremenska memorijska ranjivost|vremenska memorijska ranjivost]] zbog koje program može da ponovo oslobodi memorijsku alokaciju koja je već oslobođena.

## Primer
Modul za generisanje PDF faktura u [[Fakturis]] zauzme [[Bafer|bafer]] za naziv kupca. Ako formatiranje fakture naiđe na grešku, grana za obradu greške oslobodi bafer, ali zatim zajednički blok za čišćenje oslobodi istu alokaciju još jednom. Napadač pošalje zahtev koji aktivira tu putanju i izazove dvostruko oslobađanje.

Kontraprimer: ako modul oslobodi bafer jednom, a zatim ga pročita ili upiše, to je [[Korišćenje posle oslobađanja]].

## Napomene
- Dvostruko oslobađanje nije dereferenciranje. Greška nastaje ponavljanjem operacije oslobađanja nad istom alokacijom, čak i kada između dva poziva nije bilo čitanja ni upisa.
- Može da ošteti strukture koje [[Heap|heap]] koristi za upravljanje memorijom. Posledice mogu biti rušenje programa, čitanje ili izmena neočekivanih memorijskih lokacija, a u određenim okolnostima i izvršavanje neovlašćenog koda.
- Nastaje pri [[Ručno upravljanje memorijom|ručnom upravljanju memorijom]], gde programer mora da vodi računa da se alokacija oslobodi samo jednom.
- Čest uzrok je da više grana obrade greške ili čišćenja preuzme odgovornost za oslobađanje iste alokacije. Svaka alokacija treba da bude oslobođena samo jednom.
- MITRE CWE-672 opisuje širu klasu operacija nad resursom nakon isteka ili oslobađanja i kao demonstrativni primer uključuje dvostruko oslobađanje. U jednom od CWE hijerarhijskih prikaza CWE-415 je podvrsta CWE-672 i vodi se odvojeno od CWE-416 (Use After Free). To podržava njegovo svrstavanje u vremenske memorijske ranjivosti, iako `free()` nije dereferenciranje.
