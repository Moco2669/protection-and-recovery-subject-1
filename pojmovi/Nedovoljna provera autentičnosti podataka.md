---
tip: pojam
aliases: [insufficient verification of data authenticity, unsafe consumption of APIs]
izvor: CWE-345 Insufficient Verification of Data Authenticity; OWASP API Security Top 10:2023, API10:2023 Unsafe Consumption of APIs
status: predlog
sloj: jezgro
---
# Nedovoljna provera autentičnosti podataka (insufficient verification of data authenticity)

## Definicija
Nedovoljna provera autentičnosti podataka je [[Slabost|slabost]] u kojoj [[Komponenta sistema|komponenta sistema]] prihvata podatke kao da potiču od određenog izvora, a ne proverava da li ih je taj izvor zaista poslao i da li su usput izmenjeni.

## Primer
PayNet svako obaveštenje o uplati potpisuje tajnim ključem koji deli sa firmom [[Fakturis]]. Aplikacija, međutim, potpis ne proverava: svaki zahtev na adresu `/api/paynet/obavestenje` sa poljem `"status": "uspesno"` menja status fakture u „plaćeno“. Korisnik koji zna broj svoje fakture može sam da pošalje takav zahtev i da izbegne plaćanje, a aplikacija ga i dalje vodi kao uredno naplaćenog.

## Napomene
- Slabost se najčešće javlja na [[Tok podataka|tokovima podataka]] koji prelaze [[Granica sistema|granicu sistema]], posebno kada aplikacija veruje [[Spoljni servis|spoljnom servisu]] samo zato što zahtev izgleda kao da dolazi od njega.
- Šifrovanje veze (HTTPS) ovu slabost ne otklanja. HTTPS štiti podatke na putu, ali ne dokazuje da ih je poslao PayNet.
