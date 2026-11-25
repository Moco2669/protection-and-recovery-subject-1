---
tip: pojam
aliases: [exploit]
izvor: 'MITRE ATT&CK T1587.004, Develop Capabilities: Exploits: https://attack.mitre.org/techniques/T1587/004/; Cisco, Cisco Security Ninja White Belt, Exploits and Attacks, slajd 9: https://community.cisco.com/kxiwq67737/attachments/kxiwq67737/4561-docs-security/4408/1/cisco_security_ninja_white_belt-network_engineer.pdf'
status: prihvaćeno
sloj: jezgro
---
# Eksploit (exploit)

## Definicija
Eksploit je posebno pripremljen program, skup podataka ili niz komandi koji iskorišćava ranjivost kako bi izazvao nepredviđeno ponašanje komponente sistema.

## Primer
Modul za generisanje PDF faktura u [[Fakturis]] kopira naziv kupca iz zahteva u [[Bafer|bafer]] od 64 bajta. Napadač sastavlja HTTP zahtev čije polje sa nazivom kupca sadrži posebno pripremljene podatke dužine 200 bajtova. Podaci su konstruisani tako da [[Prekoračenje bafera|prekoračenje bafera]] prepiše susedno polje koje čuva status fakture i promeni ga u „plaćeno“. Posebno pripremljeni podaci u zahtevu predstavljaju eksploit.

## Napomene
- U ovoj bazi, **eksploit** označava sredstvo za iskorišćavanje ranjivosti: program, skup podataka ili niz komandi. **Iskorišćavanje ranjivosti** označava postupak, a [[Napad iskorišćavanjem memorijske ranjivosti|napad iskorišćavanjem memorijske ranjivosti]] obuhvata širi niz radnji napadača.
- Eksploit ne mora biti samostalan izvršni program. U primeru je to posebno pripremljen skup podataka unutar HTTP zahteva.
