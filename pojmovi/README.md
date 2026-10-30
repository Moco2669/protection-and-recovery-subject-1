# Bezbednosne kontrole: vrste i primena

Ovaj deo materijala obrađuje osam pojmova koji objašnjavaju kako razvrstavamo bezbednosne kontrole i kako ih primenjujemo na komponente informacionog sistema. Namenjen je uredniku kao pregled sadržaja i predlog za povezivanje sa zajedničkim modelom znanja i prezentacijom.

Polazni kontekst je mapa informacionog sistema sa zaposlenima, poslovnim uređajima, mrežom, razvojem aplikacije, web aplikacijom, bazom i dokumentima, nalozima i pravima, praćenjem rada i rezervnim kopijama. Fizičku osnovu čine prostorije, oprema i napajanje. Materijal se ne oslanja na raniji primer firme Atlas niti na prethodno pripremljene prezentacije.

## Obuhvat i odnosi među pojmovima

Pojmovi pripadaju dvema podelama i jednoj oblasti primene:

| Pogled na kontrole | Pojmovi | Pitanje na koje odgovaraju |
| --- | --- | --- |
| Način sprovođenja | [Tehnička](Tehnička%20kontrola.md), [Organizaciona](Organizaciona%20kontrola.md), [Kadrovska](Kadrovska%20kontrola.md), [Fizička kontrola](Fizička%20kontrola.md) | Kako se mera sprovodi? |
| Svrha | [Preventivna](Preventivna%20kontrola.md), [Detektivna](Detektivna%20kontrola.md), [Korektivna kontrola](Korektivna%20kontrola.md) | Da li mera sprečava, otkriva ili ispravlja problem i njegove posledice? |
| Oblast primene | [Kontrola pristupa](Kontrola%20pristupa.md) | Ko sme da pristupi resursu i koje radnje sme da izvrši? |

**Ista mera može istovremeno imati oznaku iz obe podele.** Provera dozvole u aplikaciji je tehnička i preventivna kontrola. Zaključavanje prostorije je fizička i preventivna kontrola. Kontrola pristupa može uključivati obe mere, kao i organizacioni postupak odobravanja prava.

Osnovni pojam „bezbednosna kontrola” povezuje se sa zajedničkim delom gradiva. Ovih osam beleški proširuje taj pojam kroz vrste i primenu.

## Veza sa komponentama sistema

Tabela daje izabrane primere primene. Ne predstavlja potpun katalog kontrola niti potvrdu da su mere već uvedene u sistem.

| Komponenta ili deo sistema | Konkretna mera | Način sprovođenja | Pretežna svrha u primeru |
| --- | --- | --- | --- |
| Zaposleni | Obuka za proveru primaoca pre slanja osetljivog dokumenta | Kadrovska | Preventivna |
| Razvoj i održavanje aplikacije | Postupak pregleda, testiranja i odobravanja izmene pre objavljivanja | Organizaciona | Preventivna |
| Ruter i zaštitni zid | Filtriranje nepotrebnih dolaznih veza | Tehnička | Preventivna |
| Web aplikacija i sistem naloga i prava | Provera dozvole za pristup svakom traženom zapisu | Tehnička | Preventivna |
| Prikupljanje zapisa o radu | Automatsko upozorenje na veliki broj neuspelih prijava | Tehnička | Detektivna |
| Skladište dokumenata i sistem rezervnih kopija | Vraćanje dokumenata iz proverene kopije uz proveru ispravnosti | Tehnička, uz organizovani postupak | Korektivna |
| Prostorija sa serverom i mrežnom opremom | Zaključavanje i ograničena dodela ključeva | Fizička, uz organizacioni postupak | Preventivna |

Jednoj komponenti obično je potrebno više kontrola, a ista kontrola može obuhvatiti više komponenti. Zato ne treba povezivati svaku vrstu kontrole sa samo jednim delom sistema.


