---
tip: pojam
aliases: [File Transfer Protocol]
izvor: IETF RFC 959, File Transfer Protocol ([RFC](https://www.rfc-editor.org/rfc/rfc959.html)); IETF RFC 2428, FTP Extensions for IPv6 and NATs ([RFC](https://www.rfc-editor.org/rfc/rfc2428.html))
status: predlog
sloj: jezgro
---
# FTP (File Transfer Protocol)

## Definicija
FTP je [[Aplikacioni protokol|aplikacioni protokol]] kojim klijent i server razmenjuju komande, odgovore i datoteke. Komande i odgovori prenose se kontrolnom vezom, a sadržaj datoteke ili listing direktorijuma zasebnom podatkovnom vezom.

## Sekundarni primeri
Korisnica Ana se FTP klijentom prijavljuje na `files.example.net` i preuzima `izvestaj.pdf`. U pasivnom režimu klijent šalje `USER ana` i `PASS` kontrolnom vezom, zatim `EPSV` da od servera dobije port za podatkovnu vezu. Komandom `RETR izvestaj.pdf` traži datoteku; njeni bajtovi stižu podatkovnom vezom. Ovaj primer je ilustrativan i ne određuje način prenosa datoteka u firmi [[Fakturis]].

## Napomene
- Kontrolna veza obično se uspostavlja ka TCP portu 21 servera i prenosi komande i odgovore. Podatkovna veza prenosi datoteke ili listing; njena adresa i port zavise od režima rada.
- U aktivnom režimu klijent komandom `PORT` ili `EPRT` saopštava na kojoj adresi i portu čeka, a server otvara podatkovnu vezu ka klijentu. U pasivnom režimu klijent šalje `PASV` ili `EPSV`, server saopštava gde čeka, a klijent otvara podatkovnu vezu ka serveru. Kod `EPSV` odgovora navodi se port; klijent koristi adresu servera sa kontrolne veze.
- `USER` i `PASS` šalju korisničko ime i lozinku. `RETR` traži preuzimanje datoteke, a `STOR` slanje datoteke na server. Ove komande idu kontrolnom vezom; sadržaj datoteke ide podatkovnom vezom.
- Brojevi poput 220, 331, 230, 227, 229, 150 i 226 jesu FTP odgovori servera, ne polja u zaglavlju datoteke. Na primer, 220 označava početnu poruku da je server spreman; 331 traži lozinku; 230 potvrđuje uspešnu prijavu; 227 i 229 odgovaraju na `PASV` i `EPSV`; 150 najavljuje početak prenosa, a 226 njegov uspešan završetak.
- Običan FTP ne šifruje komande, lozinku ni sadržaj datoteke. FTPS dodaje TLS zaštitu FTP-u, dok je SFTP zaseban protokol za prenos datoteka preko SSH-a.
