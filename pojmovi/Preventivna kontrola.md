---
tip: pojam
aliases: [Preventive control]
izvor: 'Osnov za definiciju (parafraza): ISO/IEC 27002:2022, odeljak 4.2(a), atribut Control type, https://www.iso.org/standard/75652.html; izvor za primer: CIS Controls v8.1, kontrola 6 — Access Control Management, https://www.cisecurity.org/controls/access-control-management'
---
# Preventivna kontrola (Preventive control)

## Definicija
Preventivna kontrola je bezbednosna kontrola čija je osnovna svrha da spreči narušavanje bezbednosnog svojstva resursa ili smanji mogućnost njegovog nastanka. Namenjena je sprečavanju bezbednosnog incidenta i deluje pre nego što se neželjena radnja ostvari, na primer proverom dozvole ili ograničavanjem dostupnih funkcija.

## Primer
Spoljni korisnik menja oznaku zapisa u zahtevu poslovnoj web aplikaciji i pokušava da pročita tuđe podatke.

- **Komponenta:** poslovna web aplikacija.
- **Resurs:** korisnički podaci.
- **Bezbednosni zahtev:** korisnik može da čita samo zapise za koje ima dozvolu.
- **Pretnja:** neovlašćeno čitanje tuđih podataka.
- **Ranjivost:** aplikacija proverava prijavu, ali ne proverava pravo pristupa traženom zapisu.
- **Kontrola:** provera dozvole pre vraćanja svakog zapisa i odbijanje nedozvoljenog zahteva.

## Napomene
- ISO/IEC 27002:2022, odeljak 4.2(a), preventivno dejstvo vezuje za sprečavanje nastanka incidenta. Definicija je parafraza prilagođena pojmovima resursa i bezbednosnih svojstava, a ne doslovan prevod standarda.
- Ovo je podela **prema svrsi**. Provera dozvole je istovremeno [[Tehnička kontrola|tehnička kontrola]], a deo je [[Kontrola pristupa|kontrole pristupa]].
- Preventivnu ulogu mogu imati i [[Organizaciona kontrola|organizaciona]], [[Kadrovska kontrola|kadrovska]] i [[Fizička kontrola|fizička kontrola]]. Primeri su postupak odobravanja izmena, obuka zaposlenih i zaključavanje prostorije sa serverom.
- Prevencija ne garantuje da incident neće nastati. Dopunjuju je [[Detektivna kontrola|detektivne]] i [[Korektivna kontrola|korektivne kontrole]].
- **Ideja za vizualizaciju:** zahtev → provera dozvole → dozvoljen pristup ili odbijanje.
