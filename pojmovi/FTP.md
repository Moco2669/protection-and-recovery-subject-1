---
tip: pojam
aliases: [File Transfer Protocol]
izvor: IETF RFC 959 ([RFC](https://www.rfc-editor.org/rfc/rfc959.html)); RFC 2577, FTP Security Considerations ([RFC](https://www.rfc-editor.org/rfc/rfc2577.html))
status: predlog
sloj: jezgro
---
# FTP (File Transfer Protocol)

## Definicija
FTP je [[Aplikacioni protokol|aplikacioni protokol]] za upravljanje i prenos datoteka između [[Klijentski program|klijenta]] i [[Serverski program|servera]], sa odvojenom [[FTP kontrolna veza|kontrolnom vezom]] za komande/odgovore i [[FTP veza za prenos podataka|vezom za prenos podataka]] za sadržaj datoteke ili listing.

## Sekundarni primeri
Korisnica Ana preuzima `izvestaj.pdf` sa `files.example.net` običnim FTP-om:

```text
220 Service ready
USER ana
331 Password required
PASS letmein2026
230 Login successful
EPSV
229 Entering Extended Passive Mode (|||50000|)
RETR izvestaj.pdf
150 File status okay; about to open data connection
[bajtovi datoteke prenose se odvojenom vezom]
226 Closing data connection; transfer successful
```

Primer je namerno nešifrovan; običan FTP šalje komande, korisničko ime, lozinku i sadržaj čitljivo. Lozinka `letmein2026` je izmišljena demonstraciona vrednost, nikada stvarna lozinka.

## Napomene
- U [[FTP pasivni režim|pasivnom režimu]] server saopšti port, a klijent inicira vezu; pogrešno otvoren pasivni opseg ili slabo vezivanje data veze za prijavljenu sesiju može izložiti prenos pokušaju prisluškivanja ili preuzimanja. U [[FTP aktivni režim|aktivnom režimu]] klijent saopšti adresu/port, a server inicira vezu ka klijentu; PORT/EPRT može biti zloupotrebljen za FTP bounce.
- Pasivni režim često lakši iza NAT/firewall-a jer klijent inicira obe veze. Aktivni može biti blokiran jer server inicira drugu vezu ka klijentu.
- Zloupotreba PORT/EPRT da server otvori vezu ka trećem sistemu zove se FTP bounce. Ograničiti dozvoljena odredišta, proveriti adresu i isključiti proxy FTP ako nije potreban.
- Običan FTP nema kriptografsku zaštitu. Napadač na putanji može pročitati lozinku/datoteku ili [[Napad posrednikom|MITM napadom]] izmeniti saobraćaj. Za poverljive prenose koristiti šifrovan protokol, proveravati identitet servera i ograničiti naloge.
- 
- `USER`, `PASS`, `EPSV`, `EPRT`, `RETR`, `STOR` i odgovori 220, 331, 230, 227, 229, 150, 226 pripadaju kontrolnoj razmeni, ne zaglavlju TCP-a.

- Pasivni režim izbegava da server inicira vezu ka klijentu, ali ne šifruje prenos: lažni endpoint, prisluškivanje ili MITM na putanji i dalje mogu ugroziti datoteku. Server treba da veže data vezu za autentifikovanu sesiju, ograniči opseg portova i proveri pristup.
- Zaštititi naloge, ograničiti dozvole i ažurirati krajnje sisteme.









