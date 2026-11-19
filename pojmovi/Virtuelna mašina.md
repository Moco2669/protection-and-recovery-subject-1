---
tip: pojam
aliases: [virtual machine, VM, sistemska virtuelna mašina]
izvor: 'NIST CSRC Glossary, virtual machine; NIST SP 800-125: https://csrc.nist.gov/glossary/term/virtual_machine'
status: predlog
sloj: temelj
---
# Virtuelna mašina (virtual machine, VM)

## Definicija
Virtuelna mašina je softverski realizovan računar sa virtuelnim hardverskim resursima, na kojem se izvršava sopstveni gostujući operativni sistem sa svojim jezgrom i aplikacijama.

## Primer
Ako bi se aplikacioni [[Server|server]] firme [[Fakturis]] izvršavao kao Linux virtuelna mašina na fizičkom serveru, Linux i aplikacija radili bi unutar te mašine. Hipervizor bi joj dodeljivao deo resursa fizičkog servera. Ovo je ilustrativna konfiguracija.

## Napomene
- Hipervizor je [[Sistemski softver|sistemski softver]] koji stvara i izvršava virtuelne mašine i upravlja njihovim pristupom fizičkim resursima.
- [[Hardverska platforma]] je fizički računar ispod virtuelizacije. Virtuelna mašina pripada opisu [[Sistemsko okruženje|sistemskog okruženja]] aplikacije.
- Sistemska virtuelna mašina ima sopstveno jezgro gostujućeg OS-a. [[Kontejner]] u uobičajenom modelu procesne izolacije deli jezgro okruženja na kojem radi. Izuzetak je, na primer, Windows Hyper-V izolacija: svaki kontejner izvršava se u zasebnoj optimizovanoj VM sa zasebnim jezgrom.
- Kontejner može raditi u virtuelnoj mašini: fizički server → hipervizor → VM sa Linuxom → kontejner → aplikacija.
- Ovde se definiše sistemska virtuelna mašina. JVM je aplikacijska virtuelna mašina, odnosno [[Izvršno okruženje|izvršno okruženje]] za programski kod, a ne virtuelni računar sa gostujućim OS-om.
- Virtuelizacija sama po sebi ne garantuje potpunu izolaciju; bitni su prava pristupa, deljeni resursi i podešavanja.
