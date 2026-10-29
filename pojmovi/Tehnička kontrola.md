---
tip: pojam
aliases: [technical control, technological control, tehnološka kontrola]
izvor: NIST SP 800-30 Rev. 1, Appendix B Glossary, "technical controls" (FIPS 200); ISO/IEC 27002:2022, poglavlje 8 Technological controls
status: predlog
sloj: temelj
---
# Tehnička kontrola (technical control)

## Definicija
Tehnička kontrola je [[Bezbednosna kontrola|bezbednosna kontrola]] koju izvršava hardver ili softver [[Komponenta sistema|komponente sistema]], bez učešća čoveka pri svakoj primeni.

## Primer
Firma [[Fakturis]] već ima dve tehničke kontrole: zaštitni zid na mrežnom prolazu i HTTPS. Može da uvede i proveru vlasništva fakture u aplikaciji, parametrizovane upite, proveru potpisa obaveštenja PayNet-a, prijavu na GitLab lozinkom i kodom sa telefona i šifrovanje rezervnih kopija.

Kontraprimer: pravilo „API ključevi se ne upisuju u repozitorijum“ je pravilo koje programeri treba da poštuju, pa je to [[Organizaciona kontrola|organizaciona kontrola]]. Tehnička kontrola je tek alat u GitLab-u koji automatski odbije izmenu u kojoj prepozna ključ.
