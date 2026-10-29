---
tip: pojam
aliases: [system boundary, boundary]
izvor: NIST SP 800-53 Rev. 5, Appendix A Glossary, "boundary" (CNSSI 4009) i "authorization boundary" (OMB A-130)
status: predlog
sloj: temelj
---
# Granica sistema (system boundary)

## Definicija
Granica sistema je razgraničenje koje odvaja [[Komponenta sistema|komponente sistema]], kojima organizacija upravlja i za čiju je zaštitu odgovorna, od spoljnih lica, uređaja i servisa sa kojima sistem razmenjuje podatke, ali kojima organizacija ne upravlja.

## Primer
Unutar granice sistema firme [[Fakturis]] su zaposleni, poslovni računari, mrežni prolaz, interna mreža, aplikacioni server, web aplikacija, baza, skladište dokumenata, GitLab, testno okruženje i server za rezervne kopije. Izvan granice su korisnici aplikacije i njihovi uređaji, kupci korisnika, platni servis PayNet i internet provajder.

Granični slučaj: API ključ za PayNet služi za pristup servisu izvan granice, ali ga čuva aplikacija i njime upravlja Stefan, pa je to resurs unutar granice.

## Napomene
- Tokovi podataka koji prelaze granicu zahtevaju posebnu pažnju, jer podaci dolaze od nekoga kome organizacija ne upravlja. U Fakturisu su to zahtevi korisnika i kupaca i obaveštenja PayNet-a.
- Smeštaj u oblaku ne pomera granicu sam po sebi. Kada bi Fakturis aplikaciju preselio na iznajmljenu virtuelnu mašinu, operativni sistem i aplikacija ostali bi unutar granice, jer njima upravlja firma, a fizički server provajdera bio bi izvan nje.
