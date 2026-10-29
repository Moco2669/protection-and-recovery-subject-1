---
tip: pojam
aliases: [attack]
izvor: ISO/IEC 27000:2018, 3.2 attack
status: predavanje
sloj: temelj
---
# Napad (attack)

## Definicija
Napad je niz radnji koje [[Napadač|napadač]] izvodi ili navodi druge da izvedu, u pokušaju da ostvari jednu ili više [[Pretnja po komponenti|pretnji po komponenti]]. U tom nizu napadač po potrebi iskorišćava [[Ranjivost|ranjivosti]] komponenti da bi stekao mogućnosti koje nema, dok ne bude u stanju da naruši [[Bezbednosno svojstvo|bezbednosno svojstvo]] ciljnog [[Resurs|resursa]].

## Primer
Ransomware grupa napada firmu [[Fakturis]]:
1. Šalje Jeleni e-poruku „Reklamacija na fakturu 2026-0412“ sa Word prilogom koji sadrži makro.
2. Jelena otvara prilog bez provere pošiljaoca. Makroi su dozvoljeni, a Jelena radi kao lokalni administrator, pa makro instalira program za daljinsko upravljanje. Grupa stiče kontrolu nad njenim računarom.
3. Poslovni računari i serveri su u istom segmentu mreže, pa grupa sa Jeleninog računara pristupa skladištu dokumenata i serveru za rezervne kopije.
4. Šifruje PDF fakture, ugovore i rezervne kopije.

Napad ostvaruje pretnju po komponenti „ransomware grupa narušava dostupnost poslovnih dokumenata u skladištu dokumenata“. Usput iskorišćava četiri ranjivosti: Jeleninu naviku, dozvoljene makroe, administratorska prava i nesegmentiranu mrežu.

Granični slučajevi:
- Jelena prepozna lažnu poruku i prijavi je Stefanu. Napad nije uspeo, ali to je ipak napad, jer je napad pokušaj.
- Jelena sama izveze spisak korisnika i proda ga konkurenciji. Nije iskoristila nijednu ranjivost, ali to je ipak napad.
- Pentester po ugovoru sa firmom izvodi iste korake kao ransomware grupa. Nema napadača, pa to nije napad.
