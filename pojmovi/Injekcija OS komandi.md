---
tip: pojam
aliases: [OS command injection, shell injection, injekcija komandi operativnog sistema]
izvor: 'MITRE CWE-78: https://cwe.mitre.org/data/definitions/78.html; OWASP OS Command Injection Defense Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/OS_Command_Injection_Defense_Cheat_Sheet.html; Python dokumentacija, subprocess: https://docs.python.org/3/library/subprocess.html; POSIX, Shell Command Language: https://pubs.opengroup.org/onlinepubs/9799919799/utilities/V3_chap02.html'
status: predlog
sloj: jezgro
---
# Injekcija OS komandi (OS command injection)

## Definicija
Injekcija OS komandi je [[Injekcioni napad|injekcioni napad]] u kome napadač u vrednost koju komponenta ugrađuje u komandu operativnog sistema ubacuje posebne znakove shell-a ili delove komande, kako bi shell izvršio i radnje koje je odredio napadač.

## Primer
U ilustrativnoj funkciji arhive za knjigovođu, [[Softverski proizvod|proizvod]] [[Fakturis|Fakturisa]] pravi ZIP arhivu faktura za izabrani mesec. Komandu sastavlja spajanjem teksta i predaje je shell-u na aplikacionom [[Server|serveru]], u Python-u, na primer, pozivom `subprocess.run(komanda, shell=True)`:

```
zip /tmp/arhive/<naziv>.zip fakture/2026-03/*
```

Na mesto `<naziv>` proizvod upisuje naziv arhive koji je uneo korisnik. Shell ceo tekst parsira kao komandnu liniju: razdvaja reči, proširuje `*` u spisak datoteka i tumači posebne znakove. Napadač, prijavljen kao korisnik, kao naziv arhive upiše bezopasan demonstracioni ulaz:

```text
mart; id #
```

Proizvod od njega sastavlja komandnu liniju:

```sh
zip /tmp/arhive/mart; id #.zip fakture/2026-03/*
```

Python za `shell=True` na POSIX sistemima podrazumevano koristi `/bin/sh`. Takav shell liniju čita ovako. Znak `;` završava prvu komandu, pa ona postaje `zip /tmp/arhive/mart`, bez ijedne datoteke za arhiviranje, i završava se greškom. Shell zatim izvršava drugu komandu, `id`, koja ispisuje korisnika i grupe naloga pod kojim radi proizvod. Znak `#` na početku reči započinje komentar, pa shell ostatak reda, `.zip fakture/2026-03/*`, odbacuje. Uneti podatak je tako postao sintaksa: jedna vrednost se pretvorila u dve komande i komentar. `id` ništa ne menja, ali pokazuje da napadač bira šta će se izvršiti. Demonstracija važi za POSIX shell. Na Windows-u Python za `shell=True` koristi shell iz promenljive `COMSPEC`, obično `cmd.exe`, čija su pravila drugačija. Umesto `id`, napadač bi mogao da upiše i komandu koja, na primer, čita datoteku podešavanja sa pristupnim podacima [[Spoljni servis|spoljnih servisa]], što je [[Narušavanje poverljivosti podataka|narušavanje poverljivosti]]. U opštem slučaju napadač stiče mogućnost da izvršava komande dozvoljene tom nalogu ([[Dobijanje prevelikih privilegija]]). Alat, shell i scenario su ilustracija, a ne utvrđena konfiguracija Fakturisa.

Kontraprimer: ako proizvod pokrene isti program bez shell-a i argumente preda kao listu, na primer `subprocess.run(["zip", putanja_arhive, *datoteke])`, ceo upisani naziv postaje deo jednog argumenta, `/tmp/arhive/mart; id #.zip`, odnosno neobičan naziv datoteke. Znakovi `;` i `#` tada nemaju posebno značenje i `id` se ne izvršava. Bez shell-a se ni `*` ne proširuje, pa proizvod sam navodi spisak datoteka.

## Napomene
- **Kada je komponenta ranjiva.** Potrebna su dva uslova: komanda se izvršava preko shell-a ili drugog komandnog [[Interpreter|interpretera]], i u nju se ugrađuje [[Nepouzdan ulaz|nepouzdan ulaz]] bez razdvajanja vrednosti od sintakse. Sam poziv spoljnog programa nije ranjivost. Python dokumentacija, na primer, navodi da se komanda izvršava kroz shell kada je `shell=True`, i upućuje na odeljak o bezbednosti pre takvog poziva.
- **Posebni znakovi shell-a.** OWASP navodi znakove kao `&`, `|`, `;`, `$`, `>`, `<`, `` ` ``, `\`, `!`, navodnike i zagrade. Oni služe da razdvoje ili povežu komande, da u komandu umetnu izlaz druge komande ili da preusmere ulaz i izlaz. Pravila se razlikuju između shell-ova i operativnih sistema.
- **Ubacivanje argumenata.** I bez shell-a, vrednost koja počinje crticom program može da pročita kao opciju, a ne kao naziv datoteke. MITRE to vodi kao zasebnu slabost, CWE-88 (Argument Injection), a u merama zaštite za CWE-78 upozorava i na nju.
- **Posledice i prava procesa.** MITRE kao posledicu navodi izvršavanje neovlašćenih komandi, uz čitanje i izmenu datoteka i podataka i narušavanje dostupnosti. Ubačena komanda ima prava procesa proizvoda, pa njen domet određuju prava [[Servisni nalog|servisnog naloga]] i [[Sistemsko okruženje|sistemsko okruženje]], na primer [[Kontejner|kontejner]] ili [[Sandbox|sandbox]]. CWE-78 u primerima pokazuje da program koji radi sa administratorskim pravima izvršava i ubačenu komandu sa tim pravima. Ograničenja okruženja smanjuju posledicu, ali ne uklanjaju ranjivost.
- **Zaštita.**
  - Prema OWASP-u, najbolja zaštita je izbeći poziv komandi operativnog sistema i koristiti funkciju biblioteke, na primer biblioteku za ZIP arhive.
  - Ako se program mora pozvati, pokreće se bez shell-a, a argumenti se predaju kao lista ([[Parametrizacija]]).
  - Vrednosti se proveravaju listom dozvoljenih oblika ([[Validacija ulaza]]). OWASP traži i da se dozvoljene komande navedu unapred.
  - [[Neutralizacija specijalnih elemenata|Neutralizacija]] posebnih znakova shell-a je poslednja mogućnost, jer pravila zavise od shell-a.
  - Proces radi sa najmanjim pravima koja su mu potrebna.
- „Command injection“ (CWE-77) je šira klasa ubacivanja u komande bilo kog interpretera. MITRE navodi da se taj naziv često koristi kada se misli na injekciju OS komandi.
