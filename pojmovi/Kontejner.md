---
tip: pojam
aliases: [container, application container]
izvor: 'Docker Docs: https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/; Microsoft Learn, Isolation modes: https://learn.microsoft.com/en-us/virtualization/windowscontainers/manage-containers/hyperv-container; Docker Desktop VMM: https://docs.docker.com/desktop/features/vmm/'
status: predlog
sloj: temelj
---
# Kontejner (container)

## Definicija
Kontejner je izdvojeno okruženje za izvršavanje jednog ili više procesa aplikacije sa njenim zavisnostima. U uobičajenom modelu procesne izolacije, kontejneri dele jezgro operativnog sistema na kojem se izvršavaju; postoje i realizacije sa zasebnim jezgrom po kontejneru.

## Primer
Ako bi se serverski deo [[Softverski proizvod|softverskog proizvoda]] firme [[Fakturis]] pokretao u Docker kontejneru, njegov kod i potrebne biblioteke bili bi smešteni u okruženje izdvojeno od drugih aplikacija. Kontejner bi koristio jezgro Linuxa na kojem radi. Ovo je ilustrativna konfiguracija.

## Napomene
- Kontejner je jedan od načina organizovanja [[Sistemsko okruženje|sistemskog okruženja]] aplikacije.
- Docker je primer tehnologije za rad sa kontejnerima.
- Jezgro je osnovni deo operativnog sistema koji upravlja resursima uređaja. Kod procesne izolacije kontejneri dele jezgro, a ne čitav operativni sistem: mogu imati različite biblioteke, alate i druge korisničke delove OS-a.
- Za razliku od [[Virtuelna mašina|virtuelne mašine]] sa sopstvenim gostujućim OS-om, kontejner u modelu procesne izolacije nema zasebno jezgro. To nije pravilo za sve vrste kontejnerske izolacije.
- **Izuzetak — Windows Hyper-V izolacija:** svaki kontejner izvršava se u zasebnoj optimizovanoj virtuelnoj mašini, pa efektivno koristi zasebno jezgro. Ne deli jezgro Windows domaćina. Izvor: [Microsoft Learn, Isolation modes](https://learn.microsoft.com/en-us/virtualization/windowscontainers/manage-containers/hyperv-container).
- **Linux kontejneri na Windowsu i macOS-u:** najčešće rade unutar Linux virtuelnog okruženja, na primer Linux VM koju koristi Docker Desktop. Kontejneri u tom okruženju dele njegovo Linux jezgro, a ne jezgro Windowsa ili macOS-a. Na Windowsu je čest i WSL 2, koji obezbeđuje Linux jezgro uz virtuelizaciju. To ne znači da svaki Linux kontejner dobija zasebnu VM. Izvor: [Docker Desktop VMM](https://docs.docker.com/desktop/features/vmm/).
- [[Sandbox]] opisuje bezbednosnu namenu: ograničiti šta program sme da uradi. Kontejner označava način izdvajanja izvršnog okruženja, najčešće uz deljeno jezgro. Kontejner se može koristiti u realizaciji sandboxa, ali njegova ograničenja zavise od podešavanja i modela izolacije.
- Docker kontejner pokrenut sa širokim pravima i pristupom osetljivim datotekama domaćina nije automatski bezbedno okruženje za nepouzdan kod.
- Odvojeno izvršavanje znači ograničen pristup drugim aplikacijama i njihovim podacima, a ne potpunu nezavisnost. Pristup datotekama, mreži i uređajima zavisi od podešavanja i prava procesa.
