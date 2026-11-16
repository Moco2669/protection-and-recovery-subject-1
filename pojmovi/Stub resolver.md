---
tip: pojam
aliases: [stub resolver, DNS stub resolver]
izvor: IETF RFC 8499, DNS Terminology ([RFC](https://www.rfc-editor.org/rfc/rfc8499.html))
status: predlog
sloj: jezgro
---
# Stub resolver (stub resolver)

## Definicija
Stub resolver je DNS klijentska komponenta na uređaju koja formira upit za ime i prosleđuje ga konfigurisanom [[Rekurzivni DNS resolver|resolveru]], umesto da sama prati DNS hijerarhiju.

## Primer
Pregledač traži `www.example.com`; stub resolver šalje upit resolveru i aplikaciji vraća odgovor.

## Napomene
- Obično je deo operativnog sistema ili biblioteke, ne autoritativni DNS server.
- U tipičnom modelu uređaj razmenjuje upit i odgovor sa resolverom, a resolver obavlja dalja pitanja.

