---
tip: pojam
aliases: ["elevation of privilege"]
izvor: "Microsoft, Microsoft Threat Modeling Tool threats, STRIDE model, https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats; FTN, RBS 04 Modelovanje pretnji, slajdovi 48–60. Definicija je parafraza; manifestacije po komponentama su obrazložena primena, ne doslovan tekst izvora."
---

# Dobijanje prevelikih privilegija (elevation of privilege)

## Definicija

Dobijanje prevelikih privilegija je tip pretnje pri kojem napadač stiče mogućnost izvršavanja radnji koje mu prema pravilima pristupa nisu dozvoljene, u istoj komponenti ili u drugoj komponenti sistema.

## Primer

Korisnički nalog u poslovnom proizvodu sme da pregleda dokumente, ali ne i da upravlja nalozima. Napadač preko tog naloga uspe da koristi administratorske funkcije proizvoda. Ranjivost može biti pogrešna provera prava pri obradi administratorskog zahteva ili pogrešno dodeljeno pravo. Pretnja je sticanje nedozvoljene mogućnosti upravljanja nalozima.

## Napomene

Napadač može steći nedozvoljene mogućnosti u softverskom proizvodu ili navesti proces da izvrši radnju pod pravima koja napadač nema. Isto pitanje postavlja se pri pristupu bazi i repozitorijumu: ko sme da čita, menja ili administrira njihove podatke?

Zahtev prenet tokom komunikacije može izazvati nedozvoljenu dodelu prava, ali odluku donosi komponenta koja ga obrađuje. Kada skladište modelujemo kao podatke u mirovanju, dodelu i proveru prava posmatramo u procesu ili servisu koji omogućava pristup tim podacima.

Privilegija ovde označava mogućnost izvršavanja radnje nad resursom prema pravilima pristupa. Pretnja obuhvata i sticanje prava drugog korisnika, ne samo administratorskih prava.

[[Narušavanje poverljivosti podataka]] može nastati i bez trajnog sticanja novih prava. Zato samo neovlašćeno čitanje dokumenta nije dovoljno da zaključimo da je napadač promenio svoja prava pristupa.
