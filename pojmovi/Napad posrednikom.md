---
tip: pojam
aliases: [man-in-the-middle attack, MITM attack, napad posrednikom]
izvor: NIST SP 800-63B, Authentication and Lifecycle Management, phishing-resistant authentication discussion ([NIST](https://pages.nist.gov/800-63-4/sp800-63b.html)); IETF RFC 4217, odeljak 15 ([RFC](https://www.rfc-editor.org/rfc/rfc4217.html))
status: predlog
sloj: jezgro
---
# Napad posrednikom (man-in-the-middle attack)

## Definicija
Napad posrednikom je napad u kojem napadač postavi svoju tačku komunikacije između dve strane, tako da može da prisluškuje, prosleđuje ili menja njihove poruke, dok se strane pogrešno oslanjaju na to da komuniciraju neposredno jedna s drugom.

## Primer
Ako Ana koristi običan FTP preko mreže koju napadač može da nadzire, napadač može pročitati komandu `PASS` i sadržaj datoteke ili pokušati da izmeni odgovor servera.

## Napomene
- Običan FTP ne proverava kriptografski identitet servera niti šifruje sadržaj; to olakšava prisluškivanje i aktivnu izmenu kada napadač može uticati na putanju.
- Protokol sa šifrovanim kanalom štiti saobraćaj kada se pravilno proveri identitet druge strane. Šifrovanje bez provere identiteta može i dalje dozvoliti povezivanje sa lažnim serverom.
- Zaštita uključuje proveru identiteta peer-a, sigurne ključeve/sertifikate, ažurirane klijente i servere i izbegavanje nepouzdanih mreža kada se koristi nezaštićeni protokol.



