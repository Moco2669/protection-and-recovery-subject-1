---
tip: pojam
aliases: [digital signature, potpisivanje]
izvor: 'NIST FIPS 186-5, Digital Signature Standard; NIST CSRC Glossary, digital signature'
status: prihvaćeno
sloj: temelj
---
# Digitalni potpis (digital signature)

## Definicija
Digitalni potpis je vrednost izračunata iz podataka i privatnog ključa [[Asimetrična kriptografija|asimetričnog para]], koju svako ko ima odgovarajući javni ključ može da proveri. Ispravan potpis potvrđuje da podaci nisu menjani posle potpisivanja i da ih je potpisao neko ko poseduje taj privatni ključ.

## Primer
Program za ažuriranje preuzima novu verziju aplikacije i proverava njen potpis javnim ključem proizvođača, ugrađenim u već instaliranu verziju. Napadač koji podmetne izmenjen paket na server za preuzimanje nema privatni ključ, pa provera ne prolazi i paket se ne instalira.

## Napomene
- Potpisuje se [[Kriptografska heš funkcija|heš]] podataka. Algoritmi: [[RSA]]-PSS, [[Kriptografija eliptičkih krivih#Potpisi na krivama|ECDSA, EdDSA]], postkvantni ML-DSA.
- Za razliku od [[Kod za autentifikaciju poruke|MAC-a]], potpis može da proveri svako, a napraviti samo vlasnik privatnog ključa. Zato potpis podržava neporecivost, a MAC ne. Da je potpisao baš vlasnik, zavisi od toga da privatni ključ nije procureo, pa potpis neporecivost sam ne garantuje.
- Čiji je javni ključ, potvrđuje [[Digitalni sertifikat|sertifikat]].

## Česti propusti i zaštita
- **Potpis se ne proverava ispravno**: kod proverava da potpis postoji, a ne da je ispravan, ili prihvata algoritam koji navodi sama poruka (vidi JWT u [[Kod za autentifikaciju poruke]]). *Zaštita:* provera je obavezna, a algoritam fiksiran na serveru (CWE-347).
- **Javni ključ iz same poruke.** Dokument nosi i potpis i ključ za proveru; napadač potpiše izmenjen dokument svojim ključem i priloži ga. *Zaštita:* javni ključ iz pouzdanog izvora (ugrađen, iz proverenog sertifikata).
