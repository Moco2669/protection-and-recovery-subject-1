---
tip: pojam
aliases: [network file share, file share, SMB share, mrežni disk, NAS]
izvor: nema posebne standardne definicije; karakteristike prema Microsoft Learn, What is SMB File Sharing for Windows and Windows Server?
status: predlog
sloj: jezgro
---
# Deljeni mrežni folder (network file share)

## Definicija
Deljeni mrežni folder je [[Skladište datoteka|skladište datoteka]] čije foldere računar ili mrežni uređaj deli preko mreže, tako da ih druge komponente otvaraju i menjaju kao da su na njihovom sopstvenom disku.

## Primer
Skladište datoteka firme [[Fakturis]] je mrežni uređaj u prostorijama firme. [[Zaposleni sa pristupom]] otvaraju njegove foldere sa [[Poslovni računar|poslovnog računara]]. Na Jeleninom laptopu folder sa fakturama mapiran je kao mrežni disk, pa ga ona vidi kao još jedan disk.

Kontraprimer: [[Objektno skladište|objektno skladište]] takođe čuva datoteke, ali se ne mapira kao disk. Svaki objekat se traži posebnim HTTP zahtevom.

## Napomene
**Upotreba.** Svakodnevni rad zaposlenih sa dokumentima u kancelariji. Folder se ponaša kao lokalni disk, pa ne traži poseban program.

**Čuvanje na disku.** Datoteke stoje kao obične datoteke u sistemu datoteka uređaja. Prava se zadaju po folderima i datotekama, a uređaj ne zna šta je u njima. Ko dođe do diska uređaja ili njegove kopije, čita sve.

**Pristup.** Windows računari koriste protokol SMB preko TCP/IP-a. Folder se otvara po putanji oblika `\\server\folder` ili se mapira kao mrežni disk, a pristup se odobrava nalogu zaposlenog. Svaki program koji radi pod tim nalogom ima ista prava nad folderom kao i zaposleni. U Fakturisu isti Wi-Fi koriste i posetioci, pa je uređaj na mreži dostupan i njihovim računarima.

**Komande.** Klijent traži otvaranje, čitanje, upis, preimenovanje i brisanje datoteka, kao i nad lokalnim diskom. Upita po sadržaju nema. Program koji redom šifruje sve datoteke na mapiranom disku za uređaj je samo niz običnih upisa.

Od [[Objektno skladište|objektnog skladišta]] se ne razlikuje po tome da li je u firmi ili van nje, nego po obliku podataka i načinu pristupa.

Protokol SMB je ilustrativan. Studija ne određuje kojim protokolom se folder deli.
