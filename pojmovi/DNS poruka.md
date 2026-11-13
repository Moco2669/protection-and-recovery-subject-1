---
tip: pojam
aliases: [DNS message, DNS query, DNS response]
izvor: IETF RFC 1035, odeljak 4 ([RFC](https://www.rfc-editor.org/rfc/rfc1035.html))
status: predlog
sloj: jezgro
---
# DNS poruka (DNS message)

## Definicija
DNS poruka je jedinica DNS upita ili odgovora sa zaglavljem, pitanjima i zapisima u odeljcima odgovora, nadležnosti i dodatnih podataka.

## Primer
Upit može sadržati `QNAME=www.example.com`, `QTYPE=A` i `QCLASS=IN`: traži IPv4 zapis za ime u Internet klasi. Server u odgovoru može vratiti jedan ili više A zapisa.

## Napomene
- Zaglavlje ima identifikator, zastavice i brojače odeljaka: QDCOUNT (broj pitanja), ANCOUNT (broj odgovora), NSCOUNT (broj zapisa autoritativnog odeljka) i ARCOUNT (broj dodatnih zapisa). Brojači opisuju stvarnu poruku; nisu uvek jednaki 1.
- Pitanje obično sadrži ime, tip zapisa i klasu. `A` traži IPv4 zapis, `AAAA` IPv6 zapis, a `IN` označava Internet klasu.
- Tipičan upit ima jedno pitanje, ali QDCOUNT predstavlja broj prisutnih pitanja; ne treba ga definisati kao polje koje je uvek 1.
- DNS poruke mogu se prenositi preko [[UDP]]-a ili [[TCP]]-a.

