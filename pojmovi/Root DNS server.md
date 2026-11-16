---
tip: pojam
aliases: [DNS root server, root name server, root server]
izvor: IANA, Root Name Servers ([IANA](https://www.iana.org/domains/root/servers)); IETF RFC 1034 ([RFC](https://www.rfc-editor.org/rfc/rfc1034.html))
status: predlog
sloj: jezgro
---
# Root DNS server (DNS root server)

## Definicija
Root DNS server je autoritativni DNS sistem za korensku zonu koji [[Rekurzivni DNS resolver|resolveru]] daje odgovor ili upućivanje ka serverima za vršne domene, npr. `.com` ili `.rs`.

## Primer
Za `www.example.com`, root upućuje resolver ka serverima za `.com`; ne vraća konačnu adresu sajta.

## Napomene
- Postoji 13 logičkih identiteta root servera (`a`–`m`), ali nisu to 13 mašina: IANA navodi stotine instanci širom sveta. Anycast vodi upit do odgovarajuće instance, a broj instanci se menja.
- Root sistem je globalna infrastruktura nezavisnih operatora, ne „tri servera jedne organizacije“. Organizacija može imati svoj rekurzivni resolver.
- Korisnikov uređaj obično pita resolver; resolver komunicira sa root sistemom.

