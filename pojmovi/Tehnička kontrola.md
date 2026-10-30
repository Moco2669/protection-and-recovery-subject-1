---
tip: pojam
aliases: [Technical control]
izvor: 'NIST CSRC Glossary — Technical controls; definicija iz FIPS 200: https://csrc.nist.gov/glossary/term/technical_controls'
---
# Tehnička kontrola (Technical control)

## Definicija
Tehnička kontrola je bezbednosna mera koja se prvenstveno sprovodi mehanizmima softvera, hardvera ili firmvera. Sistem izvršava proveru, ograničenje ili drugu zaštitnu funkciju prema podešavanjima i pravilima.

## Primer
Zaštitni zid firme ograničava pristup internim servisima sa interneta.

- **Komponenta:** mrežni prolaz firme — ruter i zaštitni zid.
- **Resurs:** mrežna komunikacija i podaci dostupni preko internih servisa.
- **Bezbednosni zahtev:** sa interneta su dostupni samo servisi potrebni spoljnim korisnicima.
- **Pretnja:** direktan pristup internom servisu sa interneta.
- **Ranjivost:** pravila zaštitnog zida dozvoljavaju nepotrebne dolazne veze.
- **Kontrola:** pravila filtriranja koja dozvoljavaju potrebne veze i odbijaju ostale.

## Napomene
- Ovo je podela **prema načinu sprovođenja**. Opisana kontrola ima [[Preventivna kontrola|preventivnu svrhu]].
- Tehnička kontrola može imati i detektivnu ili korektivnu svrhu: automatsko upozorenje otkriva sumnjivo ponašanje, a mehanizam vraćanja pomaže oporavku.
- Primeri iz prethodnog skupa su šifrovanje, serverska validacija ulaza, ažuriranje i bezbedna podešavanja.
- [[Kontrola pristupa]], [[Evidentiranje i praćenje rada]] i [[Rezervne kopije i oporavak]] imaju tehničke elemente, ali i postupke i odgovorne osobe.
- [[Organizaciona kontrola|Organizaciona kontrola]] određuje ko odobrava i proverava pravila zaštitnog zida.
- **Ideja za vizualizaciju:** internet → zaštitni zid → dozvoljene i blokirane veze ka servisima.
