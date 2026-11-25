---
tip: pojam
aliases: [ASLR, Address Space Layout Randomization]
izvor: 'RBS 07, Razvoj bezbednog softvera u C/C++ programskim jezicima (FTN), PDF strane 179–182 (slajdovi 184–187); Ubuntu Security Documentation, Address Space Layout Randomization: https://documentation.ubuntu.com/security/security-features/process-memory/aslr/; Linux kernel documentation, /proc/sys/kernel/: https://docs.kernel.org/admin-guide/sysctl/kernel.html#randomize-va-space; Microsoft Learn, Exploit protection reference: https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/exploit-protection-reference?view=o365-worldwide'
status: prihvaćeno
---
# Randomizacija rasporeda adresnog prostora (Address Space Layout Randomization)

## Definicija
Randomizacija rasporeda adresnog prostora je [[Tehnička kontrola]] koja pri formiranju memorijskog rasporeda procesa nasumično određuje početne adrese izabranih memorijskih oblasti, kao što su [[Stek|stek]], [[Heap|heap]] i deljene biblioteke, kako bi napadaču otežala predviđanje adresa potrebnih za iskorišćavanje [[Memorijska ranjivost|memorijske ranjivosti]].

## Primer
Napadač pokušava da iskoristi prekoračenje bafera u modulu za generisanje PDF faktura u [[Fakturis]]. Njegov cilj je da prepiše povratnu adresu i preusmeri izvršavanje na funkciju `system` iz biblioteke C, odnosno da izvede napad [[Ponovna upotreba koda|ponovne upotrebe koda]].

Pretpostavimo da je na serveru uključen ASLR i da se svaki pokušaj obrađuje u novom procesu. Prilikom pokretanja novog procesa biblioteka C smešta se na nasumično izabranu početnu adresu. Zbog toga se menja i adresa funkcije `system`, pa napadač ne može pouzdano da koristi adresu koju je saznao tokom prethodnog pokretanja procesa.

## Napomene
- ASLR je [[Preventivna kontrola|preventivna]] jer otežava pouzdano iskorišćavanje memorijske ranjivosti; ne uklanja samu ranjivost niti sprečava prekoračenje bafera.
- Randomizacija se primenjuje pri formiranju memorijskog rasporeda procesa, a ne pri svakom pozivu funkcije ili svakom HTTP zahtevu. Raspored jednog dugotrajnog procesa ostaje isti tokom njegovog rada.
- Na Linuxu kernel randomizuje početni raspored procesa, uključujući stek i heap, dok ELF učitavač randomizuje lokacije izvršnog programa i deljenih biblioteka. Da bi se randomizovala i početna adresa koda glavnog izvršnog programa, on mora biti povezan kao PIE (Position Independent Executable).
- Obim randomizacije zavisi od konfiguracije. Linux parametar `randomize_va_space` bira obuhvat: vrednost `0` isključuje ASLR, `1` randomizuje izabrane oblasti, a `2` dodatno uključuje randomizaciju heap-a.
- Efikasnost zavisi od količine nasumičnosti (entropije). Veći adresni prostor 64-bitnih procesa omogućava više mogućih rasporeda nego 32-bitni procesi, ali sam prelazak na 64 bita ne garantuje da je svaka oblast dovoljno nasumična.
- Ako napadač drugim putem sazna adresu u randomizovanoj oblasti, na primer kroz ranjivost za otkrivanje sadržaja memorije, ASLR može izgubiti deo zaštitnog dejstva. Takođe, ASLR ne sprečava napade koji ne zavise od predviđanja adresa, kao što je izmena susedne promenljive.
- ASLR otežava pronalaženje adresa ubačenog koda i postojećih instrukcija. Zato može otežati i [[Injekcija mašinskog koda|injekciju mašinskog koda]] i [[Ponovna upotreba koda]], uključujući ROP.
- [[Sprečavanje izvršavanja podataka|DEP]] deluje drugačije: ne randomizuje adrese, već sprečava izvršavanje instrukcija iz memorijskih stranica koje nisu označene kao izvršive. [[Integritet toka izvršavanja|CFI]] zasebno ograničava dozvoljene prenose kontrole. Ove kontrole se dopunjuju.
- RBS 07 prikazuje ograničenja u kojima memorijske oblasti mogu zadržati fiksne međusobne pomake, a napadač može pokušati da pogodi baznu adresu ili je otkrije. PDF strane 179–182 (slajdovi 184–187).
