| **tip** | pojam |
|---|---|
| **aliases** | cleartext transmission of sensitive information |
| **izvor** | [MITRE CWE-319 — Cleartext Transmission of Sensitive Information](https://cwe.mitre.org/data/definitions/319.html) |

# Nezaštićen prenos podataka (cleartext transmission of sensitive information)

## Definicija

Nezaštićen prenos podataka jeste slabost u kojoj komponenta sistema šalje poverljive podatke bez šifrovanja kroz komunikacioni kanal koji neovlašćena osoba može da prisluškuje.

## Primer

Zaposleni se prijavljuje u poslovnu web aplikaciju firme. Aplikacija šalje njegovo korisničko ime i lozinku serveru preko HTTP veze, bez šifrovanja.

Napadač koji je stekao mogućnost da prati saobraćaj na jednom uređaju kroz koji veza prolazi može da pročita poslatu lozinku. Prenos lozinke bez šifrovanja predstavlja konkretnu ranjivost koja omogućava narušavanje njene poverljivosti.

## Kontraprimer

Aplikacija dozvoljava slanje podataka za prijavu samo preko HTTPS veze sa ispravno podešenim TLS-om, a pregledač proverava sertifikat servera. TLS šifruje podatke tokom prenosa.

Napadač koji samo prisluškuje saobraćaj na istom delu mrežnog puta ne može iz njega neposredno da pročita lozinku. Podaci za prijavu ne šalju se prethodno preko nezaštićene HTTP veze.

## Napomene

Slabost je način prenosa poverljivih podataka. Prisluškivanje je radnja napadača kojom tu slabost može da iskoristi, a otkrivanje lozinke je posledica.

Komunikacioni kanal povezuje komponente između kojih podaci putuju. Problem može postojati i unutar mreže firme, na primer između aplikacionog servera i baze podataka; interna mreža sama po sebi ne garantuje poverljivost.

Šifrovanje prenosa štiti podatke dok putuju. Ne sprečava njihovo čitanje na kompromitovanom računaru pošiljaoca ili primaoca.
