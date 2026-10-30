---
tip: pojam
aliases: [Access control]
izvor: 'CIS Controls v8.1, kontrola 6 — Access Control Management: https://www.cisecurity.org/controls/access-control-management'
---
# Kontrola pristupa (Access control)

## Definicija
Kontrola pristupa je skup pravila i mehanizama kojima se određuje i sprovodi ko sme da pristupi resursu i koje radnje sme da izvrši. Obuhvata dodelu, proveru i ukidanje prava prema poslovnim potrebama.

## Primer
Zaposleni koristi zajedničko skladište poslovnih dokumenata.

- **Komponente:** sistem naloga i prava, skladište dokumenata i aplikacija.
- **Resurs:** ugovori, izveštaji i drugi poslovni dokumenti.
- **Bezbednosni zahtev:** zaposleni može da čita ili menja samo dokumente potrebne za njegovu ulogu.
- **Pretnja:** neovlašćeno čitanje, menjanje ili brisanje dokumenta.
- **Ranjivost:** svi zaposleni imaju ista, preširoka prava.
- **Kontrola:** dodela potrebnih prava po ulogama, provera dozvole pri pristupu i redovno preispitivanje prava.

## Napomene
- Ovo je **oblast primene kontrola**, a ne nova kategorija paralelna podelama prema svrsi i načinu sprovođenja.
- Provera dozvole je [[Tehnička kontrola|tehnička]] i [[Preventivna kontrola|preventivna kontrola]]. Odobravanje prava je organizaciona mera, a odlazak zaposlenog povezuje je sa kadrovskim postupkom.
- Autentifikacija proverava identitet; autorizacija proverava dozvoljene radnje. Uspešna prijava ne daje pristup svim podacima.
- Prava ograničavamo i nalogu aplikacije u bazi, spoljnom servisu, repozitorijumu i kopijama.
- [[Sistem za zapise o radu]] je komponenta koja čuva zapise o pristupu i omogućava pregled korišćenja prava.
- **Ideja za vizualizaciju:** matrica uloga i resursa sa dozvolama čitanja, izmene i brisanja.
