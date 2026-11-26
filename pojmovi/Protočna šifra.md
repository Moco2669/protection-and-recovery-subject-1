---
tip: pojam
aliases: [stream cipher, keystream, ključni niz]
izvor: 'NIST CSRC Glossary, stream cipher; IETF RFC 8439, ChaCha20 and Poly1305 for IETF Protocols'
status: prihvaćeno
sloj: jezgro
---
# Protočna šifra (stream cipher)

## Definicija
Protočna šifra je [[Simetrična kriptografija|simetrični]] algoritam koji iz ključa, kod savremenih šifri i iz [[Jednokratna vrednost|jednokratne vrednosti]], pravi pseudoslučajan niz bajtova (ključni niz, keystream) i šifruje poruku XOR-ovanjem sa tim nizom.

## Primer
Jedan bajt, zapisan bitovima:

```text
otvoreni tekst   01001000   (slovo H)
ključni niz      10110011
šifrat           11111011   (XOR)
šifrat ⊕ niz     01001000   (ponovo H)
```

Savremena protočna šifra je ChaCha20, u [[TLS|TLS-u]] kao ChaCha20-Poly1305. Google ju je 2014. uveo u Chrome za Android, jer većina tadašnjih telefona nije imala hardversku podršku za AES: na njima je bila oko tri puta brža od AES-GCM. Na računarima sa takvom podrškom brži je AES-GCM, pa pregledač bira šifru prema uređaju.

## Napomene
- Dešifrovanje je isti postupak: isti ključni niz XOR-uje se sa šifratom.
- Blokovska šifra u CTR [[Blokovska šifra#Režimi rada|režimu]] takođe radi kao protočna: šifruje uzastopne vrednosti brojača, a rezultat je ključni niz. Zato propusti ove beleške važe i za AES-CTR i AES-GCM.
- WireGuard VPN koristi isključivo ChaCha20-Poly1305, bez mogućnosti izbora šifre, jer izbor algoritama povećava složenost protokola (suprotan pristup od [[Kriptografska agilnost|kriptografske agilnosti]]).

## Česti propusti i zaštita
- **Ponovljen ključni niz.** Isti ključ i nonce za dve poruke daju `C1 ⊕ C2 = P1 ⊕ P2`: ključni niz nestaje, pa iz poznatog dela jedne poruke sledi druga. *Zaštita:* jedinstven nonce po poruci.
- **Izmena bez otkrivanja.** Promena bita u šifratu menja isti bit teksta: ko zna da na nekom mestu piše `iznos=0100`, pravi šifrat za `iznos=9100` bez ključa. *Zaštita:* protočna šifra samo u [[Autentifikovano šifrovanje|AEAD obliku]] (ChaCha20-Poly1305).
