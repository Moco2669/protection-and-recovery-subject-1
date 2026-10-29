# Tema i odredišni problemi

**Tema:** Integrisana sajber-bezbednost enterprise firme

**Odredišni problemi:**Zaštita sopstvenih aplikacija

* Problem: Zaštititi platformu od neželjenih načina korišćenja, eksternih napada i   
  * iskorištavanja tuđih API-ja  
  * Nad čim: Web aplikacija koja čuva korisničke podatke i rukuje sa API servisom treće strane  
  * Mera: Procenat uspešno blokiranih malicioznih zahteva na skupu predefinisanih testnih scenarija.  
* Otkrivanje slabosti  
  * Problem: Pronaći bezbednosne propuste i slabosti u konfiguraciji aplikacije i poslovnim procesima  
  * Nad čim: Poslovnim procesima u firmi i sopstvenom aplikacijom  
  * Mera: Broj otkrivenih slabosti otkrivenih u datom vremenskom roku  
* Zaštita poslovnih procesa  
  * Problem: Zaštita i oporavak od napada na sistem preko slabosti servisa koje koriste zaposleni ili sama aplikacija  
  * Nad čim: Računari u firmi  
  * Mera: Načinjena šteta nad podacima i vreme potrebno za oporavak

# Fokusna pitanja

Šta moramo da znamo da rešimo problem**:**

,,Zaštita sopstvenih aplikacija”:

* Koje su norme i uslovi za bezbedno skladištenje podataka?  
* Kako graditi i održavati aplikaciju da bi se te norme ispoštovale?   
* Kako sprečiti korisnika da radi maliciozne aktivnosti u aplikaciji?  
* Kako sistem prepoznaje maliciozne aktivnosti i kada postojeći filteri počinju da propuštaju napade?  
* Kako zaštititi endpointove i bezbedno rukovati API servisima treće strane?

,,Zaštita poslovnih procesa”:

* Kako podaci firme mogu biti ugroženi?  
* Kako funkcioniše napad spolja i na koji način se širi kroz mrežu?  
* Kako omogućiti oporavak nakon uspešnog napada ili kako ga sprečiti?  
* Kako prepoznati kompromitovane delove sistema na osnovu sumnjive komunikacije na mreži?   
* Kako iz sistema logova ustanoviti da je došlo do napada?

,,Otkrivanje slabosti”

* Kako pristupiti napadanju sistema (penetracionom testiranju)?  
* Kako se sprovodi bezbednosno testiranje nad aplikacijom?  
* Kako skeneri otkrivaju propuste i koje varijante ranjivosti im najčešće promaknu?

# Skelet pojmova

## Temelj

* Pretnja, ranjivost, rizik i slabost   
* CIA trijada  
* Socijalni inženjering, fišing i malver  
* Informaciona imovina  
* Događaj, incident i log  
* Identitet i principi kontrole pristupa  
* Kriptografija (heš, digitalni potpis…)

## Jezgro oblasti

* Word makroi i zlonamerni dokumenti  
* Autentifikacija, autorizacija i RBAC  
* Hardening sistema i uređaja  
* Enkripcija skladištenih podataka i upravljanje lozinkama  
* Bezbednosno testiranje (SAST, DAST, Fuzzing, penetraciono)  
* SIEM i centralizovano praćenje logova  
* Modelovanje pretnji  
* Upravljanje konfiguracijom (API ključevi, tokeni…)  
* Backup  
* Privilege escalation  
* Debagovanje  
* OWASP standardi, sanitizacija ulaza i XSS  
* Fizička bezbednost  
* Lateral movement  
* CVSS \- Common vulnerability scoring system

## Front

* Zero Trust arhitektura  
* Forenzika radne memorije  
* Odgovor na incidente i oporavak sistema.  
* Bezbedna distribucija i ažuriranje softvera