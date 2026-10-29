---
tip: pojam
aliases: [external system service, third-party service, servis treće strane]
izvor: NIST SP 800-53 Rev. 5, Appendix A Glossary, "external system service"
status: predlog
sloj: temelj
---
# Spoljni servis (external service)

## Definicija
Spoljni servis je softverski servis izvan [[Granica sistema|granice sistema]], kojim upravlja druga organizacija, a koji [[Komponenta sistema|komponente sistema]] koriste da bi obavile deo nekog [[Poslovni proces|poslovnog procesa]].

## Primer
PayNet je spoljni servis firme [[Fakturis]]. Aplikacija mu šalje zahtev za naplatu potpisan API ključem, PayNet obrađuje karticu kupca i javlja ishod. Fakturis ne može da proveri kod ni podešavanja PayNet-a. Može samo da kontroliše šta mu šalje, koja obaveštenja od njega prihvata i koja prava ima API ključ.

Kontraprimer: GitLab je softver drugog proizvođača, ali ga Fakturis instalira na sopstveni server i sam njime upravlja. Zato je GitLab komponenta sistema, a ne spoljni servis.

## Napomene
- Veza sa spoljnim servisom, odnosno kod koji šalje zahteve, API ključ i adresa za prijem obaveštenja, deo je aplikacije i nalazi se unutar granice sistema.
- Rizik postoji u oba smera. Napadač može da zloupotrebi spoljni servis preko naše aplikacije, na primer da preko stranice za plaćanje proverava ukradene kartice na PayNet-u. Takođe može da lažira podatke za koje aplikacija veruje da dolaze od spoljnog servisa.
