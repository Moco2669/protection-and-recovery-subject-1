---
tip: pojam
aliases: [runtime environment, runtime]
izvor: 'Microsoft Learn, What is managed code?: https://learn.microsoft.com/en-us/dotnet/standard/managed-code'
status: predlog
sloj: temelj
---
# Izvršno okruženje (runtime environment)

## Definicija
Izvršno okruženje je softver koji izvršava programski kod aplikacije i pruža mu usluge potrebne tokom rada, kao što je automatsko upravljanje memorijom.

## Primer
Ako bi [[Softverski proizvod|softverski proizvod]] firme [[Fakturis]] bio napisan u C#, izvršavao bi se uz .NET izvršno okruženje, koje bi upravljalo memorijom njegovih objekata. Ovo je ilustrativna mogućnost, a ne utvrđena tehnologija firme.

## Napomene
- Primeri su JVM za Javu, .NET za C# i Python interpreter, odnosno program koji izvršava Python kod.
- Izvršno okruženje odnosi se na izvršavanje programskog koda. [[Sistemsko okruženje]] opisuje OS, kontejner ili virtuelnu mašinu u kojima aplikacija radi.
- Aplikacijska virtuelna mašina, poput JVM-a, izvršava programski kod. Virtuelna mašina sa sopstvenim OS-om predstavlja virtuelni računar. To su različiti pojmovi.
- Automatsko upravljanje memorijom smanjuje potrebu da programer ručno oslobađa memoriju, ali ne garantuje odsustvo svih grešaka i ranjivosti.
- Pristup datotekama, mreži i uređajima i dalje zavisi od prava procesa i ograničenja operativnog sistema.
