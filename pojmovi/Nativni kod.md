---
tip: pojam
aliases: [native code, machine code]
izvor: 'Microsoft Learn, Managed execution process: https://learn.microsoft.com/en-us/dotnet/standard/managed-execution-process'
status: predlog
sloj: temelj
---
# Nativni kod (native code)

## Definicija
Nativni kod je programski kod u obliku instrukcija koje procesor određenog tipa računara može neposredno da izvršava.

## Primer
Ako bi deo [[Softverski proizvod|softverskog proizvoda]] firme [[Fakturis]] bio napisan u C++ i preveden za procesor njegovog servera, dobijeni kod bio bi nativni kod. Ovo je ilustrativna mogućnost, a ne utvrđena tehnologija firme.

## Napomene
- Izvorni kod je zapis programa koji programer piše. Prevođenjem može nastati nativni kod koji izvršava procesor.
- Nativni kod se vezuje za tip procesora. Kod namenjen jednom tipu procesora ne mora raditi na drugom.
- Nativni kod ne znači automatski nebezbedan kod. C/C++ i Rust mogu se prevesti u nativni kod, ali pružaju različite zaštite od pogrešnog korišćenja memorije.
- I kod aplikacija na platformama poput .NET-a, izvršno okruženje može tokom rada prevoditi kod u nativne instrukcije.
