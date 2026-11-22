---
tip: pojam
aliases: [IoT device, Internet of Things device, uređaj interneta stvari]
izvor: 'NIST CSRC Glossary, IoT device: https://csrc.nist.gov/glossary/term/iot_device'
status: predlog
sloj: temelj
---
# IoT uređaj (Internet of Things device)

## Definicija
IoT uređaj je fizički uređaj koji ima najmanje jedan senzor ili aktuator za neposrednu interakciju sa fizičkim svetom i najmanje jedan mrežni interfejs za razmenu podataka.

## Primer
Mrežna kamera pretvara svetlost u digitalni video i šalje ga preko mreže. Pametni termostat očitava temperaturu i upravlja grejanjem. Povezani industrijski kontroler može na osnovu merenja upravljati ventilom ili motorom.

Kontraprimer: merač temperature bez mrežnog interfejsa jeste specijalizovani uređaj, ali nije IoT uređaj prema ovoj definiciji.

## Napomene
- Senzor meri pojavu u fizičkom svetu, na primer temperaturu. Aktuator izaziva fizičku promenu, na primer otvara ventil.
- Mrežni interfejs može biti Ethernet, Wi-Fi ili Bluetooth. Uređaj ne mora biti neposredno dostupan sa interneta.
- IoT uređaj je [[Hardverska platforma|hardverska platforma]]. Softver koji na njemu obrađuje očitavanja ili upravlja aktuatorom može biti [[Procesna jedinica|procesna jedinica]] u dijagramu toka podataka.
- I ovde razlikujemo tri nivoa: fizički uređaj; [[Sistemsko okruženje|sistemsko okruženje]], na primer ugrađeni OS i podešavanja; [[Aplikativni softver|aplikativni softver]] za konkretan zadatak. Neki jednostavni uređaji nemaju zaseban OS.
- Ilustracija toka: senzor šalje temperaturu, softver termostata poredi je sa zadatom vrednošću i šalje komandu grejanju.
- Za bezbednosnu analizu proveravamo ko može čitati merenja, menjati komande i ažurirati softver, kao i kojim drugim komponentama uređaj može pristupiti preko mreže. Pogrešna komanda može promeniti fizičko stanje, a ne samo podatke.
- Ovi primeri ne uvode IoT uređaje kao utvrđene komponente firme [[Fakturis]].

## Kako uređaj radi
Senzor šalje očitavanje ugrađenom softveru. Softver obrađuje podatke, a preko mreže može razmenjivati merenja i komande sa aplikacijom ili [[Spoljni servis|spoljnim servisom]]. Aktuator izaziva fizičku promenu na osnovu komande. Ne mora svaki uređaj imati i senzor i aktuator: mrežna kamera može samo prikupljati i slati snimak.

Kod termostata, očitana i zadata temperatura predstavljaju ulaze, softver za poređenje je [[Procesna jedinica|procesna jedinica]], a komanda grejanju je izlazni [[Tok podataka|tok podataka]]. Aplikacija na telefonu može menjati zadatu temperaturu neposredno preko mreže ili posredstvom spoljnog servisa. Lokalna i udaljena obrada zavise od konstrukcije uređaja.

## Šta napad ugrožava
| Svojstvo | Ilustrativna posledica |
| --- | --- |
| Poverljivost | Neovlašćen pristup snimku kamere otkriva ljude i njihove aktivnosti. |
| Integritet | Izmenjeno merenje ili komanda može izazvati pogrešnu fizičku radnju. |
| Dostupnost | Prekid rada ili veze onemogućava nadzor ili daljinsko upravljanje. |

Napad ne mora fizički oštetiti uređaj. Posledice po opremu, ljude i poslovanje zavise od namene i ugrađenih zaštita; gubitak mreže ne znači automatski prestanak lokalnog rada. Okvir rizika: [NISTIR 8228](https://doi.org/10.6028/NIST.IR.8228). Primeri su nastavne ilustracije.

## Kako se uređaj štiti
- **Pristup i podaci:** jedinstveni pristupni podaci, ograničene komande i šifrovana komunikacija.
- **Softver:** ažuriranja uz proveru porekla i integriteta; pri nabavci proveriti koliko dugo proizvođač pruža podršku.
- **Mreža:** poseban segment uz pravila koja ograničavaju komunikaciju sa poslovnim sistemima.
- **Nadzor i oporavak:** pratiti promene i neuobičajen rad, sačuvati proverena podešavanja i planirati bezbedno izdvajanje i vraćanje uređaja u rad.

Proizvođač obezbeđuje mogućnosti zaštite, administrator ih podešava, a korisnik upravlja svojim pristupnim podacima. Ako podrška prestane, potrebno je proceniti ograničavanje upotrebe ili zamenu uređaja. Osnova za sposobnosti zaštite: [NISTIR 8259A, tabela 1](https://doi.org/10.6028/NIST.IR.8259A); mrežne mere i oporavak primenjuju se prema konkretnom okruženju.

## Ilustrativan scenario: napad na termostat
Pretpostavimo da je upravljački interfejs pametnog termostata dostupan napadaču preko mreže, a da fabrička lozinka nije promenjena. Napadač se prijavljuje i menja zadatu temperaturu. Time narušava integritet komandi i može poremetiti grejanje. Ovo je hipotetički primer, a ne opis stvarnog incidenta ili utvrđene opreme firme Fakturis.

Zaštita obuhvata jedinstvenu lozinku, ažuriranja softvera i ograničavanje pristupa upravljanju na ovlašćene korisnike. Odvajanje IoT uređaja u poseban mrežni segment uz pravila pristupa ograničava njegovu komunikaciju sa poslovnim serverima. Napad na te servere nije automatska posledica: zavisi od mrežne dostupnosti i njihovih ranjivosti.

Izmene podešavanja treba pratiti. Pri oporavku uređaj se izdvaja iz mreže, vraćaju se proverena podešavanja i menjaju pristupni podaci pre ponovnog povezivanja. Ako postoji sumnja u izmenu softvera, potrebno je vratiti proveren softver prema uputstvu proizvođača ili zameniti uređaj; sama promena lozinke ne dokazuje da je uređaj bezbedan. Proveravaju se i druge komponente kojima je mogao pristupiti.

Osnova za kontrole pristupa, konfiguracije, ažuriranja i praćenja stanja: [NISTIR 8259A, tabela 1](https://doi.org/10.6028/NIST.IR.8259A). Segmentacija mreže i postupak oporavka ovde su primenjeni na nastavni scenario.
