---
tip: pojam
aliases: ["improper authentication"]
izvor: "MITRE CWE-287: Improper Authentication, https://cwe.mitre.org/data/definitions/287.html"
---

# Neispravna autentifikacija (improper authentication)

## Definicija

Neispravna autentifikacija je [[Slabost|slabost]] pri kojoj komponenta prihvata identitet učesnika iako potrebna provera identiteta izostaje ili se ne sprovodi ispravno.

## Primer

Sistem za upravljanje nalozima treba da utvrdi identitet učesnika pre nego što uspostavi prijavu. Ako prihvati navedeni identitet bez provere da učesnik može valjano da ga dokaže, drugi učesnik može se predstaviti kao on. Kada određena komponenta omogućava takvo ponašanje, u njoj postoji konkretna ranjivost. Pretnja po toj komponenti je lažno predstavljanje učesnika.

## Napomene

Način dokazivanja identiteta zavisi od komponente i zahteva zaštite. Ovaj pojam obuhvata izostale i pogrešno sprovedene provere, nezavisno od konkretnog mehanizma autentifikacije.

Autentifikacija se odnosi na identitet učesnika. [[Neispravna kontrola pristupa]] odnosi se na dopuštanje radnje nad resursom, čak i kada je identitet ispravno utvrđen.
