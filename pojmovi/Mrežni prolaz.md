---
tip: pojam
aliases: [network gateway, gateway, boundary protection device, ruter i zaštitni zid]
izvor: NIST SP 800-53 Rev. 5, Appendix A Glossary, "boundary protection device"; CIS Critical Security Controls v8, Glossary, "network devices"
status: predlog
sloj: temelj
---
# Mrežni prolaz (network gateway)

## Definicija
Mrežni prolaz je mrežna komponenta sistema koja povezuje mrežu organizacije sa internetom i, prema zadatim pravilima, propušta, odbija ili preusmerava saobraćaj između njih.

## Primer
Mrežni prolaz firme [[Fakturis]] je jedan uređaj koji je istovremeno ruter i zaštitni zid. Zahteve korisnika i kupaca sa interneta na portu 443 (HTTPS) preusmerava ka aplikacionom serveru, a ostale dolazne zahteve odbija. Kroz njega prolazi i sav saobraćaj zaposlenih ka internetu, kao i zahtevi aplikacije ka PayNet-u i obaveštenja koja PayNet šalje nazad.

Kontraprimer: mrežni preklopnik u server sobi takođe prenosi saobraćaj, ali povezuje uređaje unutar firme, a ne firmu sa internetom. On je deo [[Interna mreža|interne mreže]].

## Napomene
- Sav saobraćaj između firme i interneta prolazi kroz mrežni prolaz, uključujući zahteve web aplikacije ka PayNet-u. PayNet ipak nije deo ovog prolaza: prolaz samo prenosi saobraćaj, a PayNet-om upravlja druga firma.
- U [[Fakturis]] je administratorski panel prolaza dostupan sa interneta, sa fabričkom lozinkom.
