---
tip: pojam
aliases: [Transmission Control Protocol]
izvor: IETF RFC 9293, Transmission Control Protocol ([RFC](https://www.rfc-editor.org/rfc/rfc9293.html))
status: predlog
sloj: jezgro
---
# TCP (Transmission Control Protocol)

## Definicija
TCP je [[Transportni protokol|transportni protokol]] koji pruža pouzdan, uređen [[Tok bajtova|tok bajtova]] između krajnjih programa.

## Primer
Pregledač šalje HTTP/1.1 zahtev Fakturisu preko TCP-a. TCP dostavlja bajtove redom i ponovo prenosi izgubljene delove; HTTP određuje kako se bajtovi tumače kao zahtev i odgovor.

## Napomene
- [[Broj sekvence TCP|Broj sekvence]] identifikuje pozicije bajtova, a ACK broj označava sledeću poziciju koju primalac očekuje.
- [[TCP prozor]] oglašava bajtni opseg koji je primalac spreman da primi. Ne određuje veličinu segmenta niti broj bajtova do pojedinačne ACK poruke.
- [[TCP početni redni broj]] bira se zasebno za svaku stranu veze; njegove vrednosti su ilustrativne i u stvarnoj vezi nisu unapred zadati brojevi.
- TCP zaglavlje sadrži izvorni i odredišni port, redni i ACK broj, data offset, rezervisana polja, zastavice, prozor, kontrolnu sumu i hitni pokazivač; opcije su dodatne, a payload sledi zaglavlje.
- Portovi pripadaju transportnom sloju i identifikuju krajnje programe, iako aplikacije koriste te portove za izbor usluge.
- TCP pouzdanost ne znači da je sadržaj bezbedan niti da je pošiljalac kriptografski autentifikovan.

