---
tip: pojam
aliases: [DEP, Data Execution Prevention]
izvor: 'RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), PDF strana 164; Microsoft Learn, Data Execution Prevention: https://learn.microsoft.com/en-us/windows/win32/memory/data-execution-prevention; Microsoft Learn, Determine hardware DEP is available: https://learn.microsoft.com/en-us/troubleshoot/windows-client/performance/determine-hardware-dep-available; Ubuntu Security Documentation, Process and memory protections: https://documentation.ubuntu.com/security/security-features/process-memory/'
status: prihvaćeno
sloj: jezgro
---
# Sprečavanje izvršavanja podataka (Data Execution Prevention)

## Definicija
Sprečavanje izvršavanja podataka je [[Tehnička kontrola]] koja najčešće uz podršku procesora označava odabrane memorijske stranice kao neizvršive i time sprečava izvršavanje instrukcija iz njih.

## Primer
Modul za generisanje PDF faktura u [[Fakturis]] kopira naziv kupca u lokalni [[Bafer|bafer]] od 64 bajta na [[Stek|steku]]. Napadač šalje naziv od 200 bajtova, čiji početni deo sadrži mašinske instrukcije, a završni deo prepisuje sačuvanu povratnu adresu tako da pokazuje na početak bafera. Pretpostavimo da je na serveru uključen DEP i da je stranica steka označena kao neizvršiva. Kada funkcija završi, program pokušava da izvršava instrukcije sa adrese bafera. Procesor odbija izvršavanje instrukcija iz te memorijske stranice i izaziva izuzetak. Ako se izuzetak ne obradi, proces se prekida.

Kontraprimer: ako napadač umesto toga preusmeri povratnu adresu na funkciju `system` u biblioteci, DEP ne reaguje, jer se izvršava postojeći izvršivi kod ([[Ponovna upotreba koda]]).

## Napomene
- DEP je [[Preventivna kontrola|preventivna]] jer sprečava izvršavanje instrukcija iz memorijskih stranica koje nisu označene kao izvršive. Ne sprečava prekoračenje bafera, prepisivanje povratne adrese ni druge upise van granica.
- Hardverska podrška za zabranu izvršavanja poznata je kao NX (No-eXecute) ili XD (eXecute Disable), u zavisnosti od proizvođača procesora. NX i XD su nazivi hardverske mogućnosti, a ne aliasi za DEP. DEP je mehanizam zaštite operativnog sistema koji koristi tu mogućnost kada je dostupna.
- Na Windows sistemima heap i stek su, po pravilu, neizvršivi. Ako program pokuša da izvrši instrukcije iz zaštićene stranice, nastaje izuzetak zbog nedozvoljenog pristupa memoriji; ako ga program ne obradi, proces se prekida.
- DEP nije isto što i W⊕X. DEP sprečava izvršavanje iz stranica bez dozvole izvršavanja; W⊕X je strože pravilo prema kome nijedna stranica ne sme istovremeno biti upisiva i izvršna.
- DEP sam po sebi ne sprečava [[Ponovna upotreba koda|ponovnu upotrebu koda]], jer se kod takvog napada izvršavaju postojeće instrukcije iz memorijskih oblasti koje su već izvršive. [[Integritet toka izvršavanja|CFI]] može da ograniči nedozvoljene prenose kontrole, dok DEP ograničava izvršavanje iz neizvršivih stranica. DEP takođe ne sprečava napade koji menjaju podatke, a ne pokušavaju da izvrše instrukcije iz neizvršive stranice.
- Programi koji generišu mašinski kod tokom izvršavanja, na primer JIT kompajleri, moraju eksplicitno da obezbede odgovarajuću dozvolu izvršavanja za memorijske stranice koje sadrže generisani kod. To je važan zahtev kompatibilnosti, a ne dokaz da je DEP zaobiđen.
- U primeru za [[Fakturis]] pretpostavlja se da je DEP uključen i da je stranica steka neizvršiva; to nije utvrđena konfiguracija proizvoda ili servera.
