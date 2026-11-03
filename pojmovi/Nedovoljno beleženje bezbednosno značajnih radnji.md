---
tip: pojam
aliases: ["insufficient logging"]
izvor: "MITRE CWE-778: Insufficient Logging, https://cwe.mitre.org/data/definitions/778.html"
---

# Nedovoljno beleženje bezbednosno značajnih radnji (insufficient logging)

## Definicija

Nedovoljno beleženje bezbednosno značajnih radnji je [[Slabost|slabost]] pri kojoj komponenta ne stvara zapise potrebne da se određene radnje povezane sa zaštitom resursa kasnije uoče, povežu sa raspoloživim podacima o izvršiocu ili istraže.

## Primer

Pravila organizacije zahtevaju da se za izmenu poslovnog zapisa može naknadno proveriti ko je zatražio izmenu, kada i sa kojim ishodom. Ako proizvod sačuva samo novo stanje, a [[Sistem za zapise o radu|sistemu za zapise o radu]] ne prosledi potrebne detalje, ti podaci ne postoje ni u [[Skladište zapisa|skladištu zapisa]]. Posle nedozvoljene izmene radnja se ne može razjasniti na osnovu tih zapisa. Nedostatak ne omogućava nužno samu izmenu, nego otežava njeno otkrivanje i istraživanje.

## Napomene

Stvaranje zapisa i njihovo analiziranje dva su koraka. Ova beleška izdvaja prvi: ako zapisi postoje, ali ih niko ne analizira, reč je o drugom nedostatku, koji se može obraditi zasebno.

Zapisi mogu podržati [[Detektivna kontrola|detektivnu kontrolu]], ali samo beleženje ne znači da je radnja blokirana niti samo po sebi garantuje neporecivost.

U zapise se ne upisuju lozinke, tajni ključevi ni jednokratni kodovi. Zaštita, obim i rok čuvanja zapisa zavise od njihove namene i vrste podataka.
