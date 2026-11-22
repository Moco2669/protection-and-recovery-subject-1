---
tip: pojam
aliases: [hardware platform]
izvor: 'NIST CSRC Glossary, hardware: https://csrc.nist.gov/glossary/term/hardware'
status: predlog
sloj: temelj
---
# Hardverska platforma (hardware platform)

## Definicija
Hardverska platforma je fizički uređaj sa procesorom, memorijom i drugim fizičkim delovima koji omogućavaju izvršavanje softvera.

## Primer
U firmi [[Fakturis]] fizički računar na kojem radi aplikacioni [[Server|server]] predstavlja hardversku platformu za izvršavanje [[Softverski proizvod|softverskog proizvoda]].

## Napomene
- U opisu softverske [[Procesna jedinica|procesne jedinice]] hardverska platforma odgovara na pitanje: na kakvom uređaju se softver izvršava?
- Za potrebe analize koristimo praktičnu podelu prema **osnovnoj ulozi uređaja i načinu upotrebe**. Najpre razlikujemo opštu obradu podataka od namenske funkcije. Među uređajima opšte namene posebno izdvajamo telefone i tablete zbog načina lične upotrebe u pokretu. To nije podela po jednom fizičkom svojstvu niti univerzalna klasifikacija bez preklapanja.

| Grupa | Kriterijum izdvajanja | Primeri | Šta je bitno za bezbednost |
| --- | --- | --- | --- |
| Računari opšte namene i fizički serveri | Opšta obrada podataka za različite radne zadatke ili pružanje mrežnih usluga. U ovoj podeli ovde ostaju i laptopi. | Laptop, stoni računar, fizički aplikacioni server. | Korisnički podaci, datoteke, mrežni servisi i prava pristupa. |
| Mobilni uređaji | Posebno izdvojeni računari opšte namene za ličnu upotrebu u pokretu, sa baterijskim radom i integrisanim interfejsima poput ekrana na dodir, kamere i određivanja lokacije. Izdvaja ih obrazac upotrebe, a ne sama prenosivost. | Pametni telefon, tablet. | Lični i poslovni podaci na istom uređaju, pristup senzorima i gubitak uređaja. |
| IoT i drugi specijalizovani uređaji | Unapred određena funkcija umesto opšteg korisničkog rada. Kod IoT-a ta funkcija uključuje merenje fizičkog sveta ili upravljanje njime i mrežnu razmenu podataka. | Mrežna kamera, pametni termostat, povezani industrijski kontroler. | Integritet merenja i komandi, kontinuitet fizičke funkcije, mrežni pristup i ažuriranje softvera. |

- **Kako odlučujemo:** termostat izdvajamo zbog namenske funkcije merenja i upravljanja grejanjem; telefon zbog lične mobilne upotrebe; laptop zbog opšteg računarskog rada. Broj procesorskih jezgara, veličina memorije ili prisustvo kamere nisu kriterijumi ove podele.
- Laptop je prenosiv, ali ga u ovoj nastavnoj podeli svrstavamo u računare opšte namene. Telefon takođe ima senzore, ali ga njihovo prisustvo samo po sebi ne premešta u grupu IoT uređaja. Osobine se preklapaju; za konkretan uređaj navodimo dominantnu ulogu i stvarne mogućnosti.

- [[IoT uređaj]] povezuje merenje ili upravljanje fizičkim svetom sa računarskom mrežom. Specijalizovani uređaj bez mrežnog interfejsa nije IoT uređaj prema definiciji koju koristimo.
- Fizički server pripada hardveru. [[Virtuelna mašina]] pripada [[Sistemsko okruženje|sistemskom okruženju]], a naziv [[Server|server]] označava ulogu koju može imati fizički ili virtuelni računar.
- Operativni sistem i drugi [[Sistemski softver|sistemski softver]] pripadaju sistemskom okruženju, a ne hardveru.
- Vrsta uređaja određuje raspoložive resurse i fizičke mogućnosti. Pravo aplikacije da ih koristi kontroliše sistemsko okruženje.
