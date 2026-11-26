---
tip: pojam
aliases: [asymmetric cryptography, public-key cryptography, kriptografija javnog ključa, javni ključ, privatni ključ, par ključeva, key pair]
izvor: 'NIST SP 800-175B Rev. 1, odeljak 3; NIST CSRC Glossary, asymmetric cryptography'
status: prihvaćeno
sloj: temelj
---
# Asimetrična kriptografija (asymmetric cryptography)

## Definicija
Asimetrična kriptografija je skup algoritama u kojima se koristi par povezanih ključeva: javni, koji sme da zna svako, i privatni, koji vlasnik drži u tajnosti i koji se iz javnog ne može praktično izračunati.

## Primer
Administrator upiše svoj javni [[SSH]] ključ na [[Server|server]], a privatni ostaje na njegovom [[Poslovni računar|računaru]]. Pri prijavi server proverava da administrator ima privatni ključ, a da ga nikad ne vidi. Krađa javnog ključa sa servera ne omogućava prijavu.

## Napomene
- Upotrebe: [[Digitalni potpis|potpis]] (privatnim ključem se potpisuje, javnim proverava), [[Diffie-Hellman razmena ključeva|dogovor zajedničkog ključa]] i [[Mehanizam enkapsulacije ključa|enkapsulacija ključa]].
- Bezbednost počiva na teškim matematičkim problemima: rastavljanju broja na činioce ([[RSA]]) i diskretnom logaritmu, klasično ili na [[Kriptografija eliptičkih krivih|eliptičkim krivama]]. Kvantni računar rešava oba ([[Postkvantna kriptografija]]).
- Spora je i radi nad kratkim podacima, pa štiti ključeve, a podatke šifruje simetrična kriptografija ([[Hibridno šifrovanje]]).
- Javni ključ ne mora biti tajan, ali mora biti autentičan; tu vezu potvrđuje [[Digitalni sertifikat|sertifikat]].

## Česti propusti i zaštita
- **Prihvatanje nepoznatog ključa.** Korisnik na upozorenje „host key changed“ odgovori „yes“. Ako je to bio [[Napad posrednikom|posrednik]], napadač vidi celu sesiju. *Zaštita:* otisak ključa servera proverava se iz drugog izvora; ključevi servera se unapred distribuiraju.
- **Privatni ključ bez zaštite.** Privatni SSH ključ bez lozinke ostaje u javnom repozitorijumu ili rezervnoj kopiji. *Zaštita:* ključ zaštićen lozinkom ili u hardverskom ključu; odmah zameniti ključ koji je procureo.
