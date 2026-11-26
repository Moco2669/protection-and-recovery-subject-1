---
tip: pojam
aliases: [interpreter, interpretator, interpreter jezika]
izvor: 'Nystrom, Crafting Interpreters, 2021, poglavlje 2: https://craftinginterpreters.com/a-map-of-the-territory.html; OWASP Injection Prevention Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Injection_Prevention_Cheat_Sheet.html'
status: predlog
sloj: temelj
---
# Interpreter (interpreter)

## Definicija
Interpreter je program ili deo programa koji tokom rada izvršava naredbe ili izračunava izraze nekog jezika, polazeći od teksta koji je primljen ili sastavljen tokom rada, ili od strukture koju je od takvog teksta prethodno napravio [[Parser|parser]].

## Primer
U ilustrativnim funkcijama [[Fakturis|Fakturisa]] [[Softverski proizvod|softverski proizvod]] predaje tekst većem broju interpretera: shell na aplikacionom [[Server|serveru]] izvršava komandu za pravljenje ZIP arhive faktura, [[Mehanizam za šablone|mehanizam za šablone]] izračunava izraze u tekstu podsetnika, a biblioteka za [[XPath]] izračunava izraz kojim se biraju fakture iz XML dokumenta.

Kontraprimer: XML parser koji od uvezene e-fakture samo napravi stablo nije interpreter. On utvrđuje strukturu, ali ne izvršava naredbe zapisane u dokumentu.

## Napomene
- **Parser i interpreter.** Parser utvrđuje strukturu ulaza, a interpreter izvršava ili izračunava ono što ta struktura opisuje. Parsiranje prethodi interpretiranju, ali ga ne mora obavljati isti program. Interpreter može sam da parsira tekst, može da obilazi stablo koje je napravio poseban parser, a može da izvršava i međuoblik, na primer bajtkod u koji je izvorni kod prethodno preveden.
- **Posledice zavise od mogućnosti i prava.** Šta ubačen deo ulaza može da izazove zavisi od radnji koje jezik i konkretan interpreter omogućavaju i od prava procesa u kome interpreter radi. Komanda shell-a ili izraz šablona mogu da pokrenu radnje u operativnom sistemu, u granicama prava [[Servisni nalog|servisnog naloga]] i [[Sistemsko okruženje|sistemskog okruženja]] programa. Isti jezik u ograničenom okruženju, na primer u [[Sandbox|sandboxu]], omogućava manje. Videti [[Injekciona ranjivost]].
- Baza podataka je interpreter za svoj [[Upitni jezik|upitni jezik]]: upit tumači i izvršava ga.
- [[Izvršno okruženje]] izvršava kod same aplikacije. Interpreter u ovoj belešci tumači tekst koji aplikacija sastavi ili primi tokom rada. Python interpreter može da ima obe uloge, ali za bezbednost je bitna druga: da li tekst koji se izvršava može da sadrži [[Nepouzdan ulaz|nepouzdan ulaz]].
