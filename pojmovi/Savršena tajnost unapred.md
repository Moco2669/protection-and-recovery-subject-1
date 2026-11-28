---
tip: pojam
aliases: [perfect forward secrecy, forward secrecy, PFS, tajnost unapred, unapred tajnost]
izvor: 'NIST CSRC Glossary, perfect forward secrecy; IETF RFC 8446, odeljak 1.2 i Appendix E.1'
status: prihvaćeno
sloj: jezgro
---
# Savršena tajnost unapred (perfect forward secrecy, PFS)

## Definicija
Savršena tajnost unapred je svojstvo [[Protokol|protokola]] po kojem kasnije otkrivanje dugotrajnih tajni, pre svega privatnog ključa servera, ne omogućava dešifrovanje ranije snimljenih sesija.

## Primer
Greška Heartbleed u OpenSSL-u (2014) omogućavala je čitanje memorije servera, pa i privatnog ključa sertifikata. Ko je ranije snimao saobraćaj servera koji je koristio RSA prenos ključa, tim ključem je mogao da dešifruje sve snimljene sesije. Kod servera sa efemernim ECDHE razmenama ukradeni ključ je omogućavao samo buduće lažno predstavljanje, ne čitanje prošlih sesija.

## Napomene
- Svojstvo daje [[Diffie-Hellman razmena ključeva|efemerni DH]]: ključevi sesije izvode se iz privremenih tajni koje se posle sesije brišu, a dugotrajni ključ služi samo za potpis. U TLS 1.3 ga ima svaka veza sa (EC)DHE.
- Ne štiti od napadača koji može da reši samu razmenu iz snimka, npr. budućim kvantnim računarom ([[Prikupi sada dešifruj kasnije]]).

## Česti propusti i zaštita
- **Ključevi za nastavak sesija koji se ne menjaju.** TLS 1.2 serveri šifruju tikete za nastavak sesije (session ticket) istim ključem danima; ko ga ukrade, čita sve sesije iz tog perioda. *Zaštita:* česta zamena ključa tiketa ili TLS 1.3.
