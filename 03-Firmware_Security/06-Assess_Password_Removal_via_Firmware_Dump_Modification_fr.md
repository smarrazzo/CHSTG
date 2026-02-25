# Évaluer la suppression du mot de passe via modification du dump firmware

|ID          |
|------------|
|CHSTG-FIRM-06|

## Résumé

Ce contrôle vise à évaluer si la protection par mot de passe BIOS/UEFI peut être supprimée par extraction et modification d'un dump du micrologiciel lorsque l'accès physique au système est disponible.

## Objectifs du test
- Déterminer si le micrologiciel BIOS/UEFI peut être accédé de l'extérieur
- Identifier si les outils de dump firmware sont compatibles avec l'appareil
- Évaluer si la suppression du mot de passe par modification du firmware est documentée publiquement
- Évaluer le risque global de contournement du mot de passe au niveau firmware

## Comment tester
1. Identifier la référence de la puce de stockage BIOS/UEFI (à partir des étapes d'identification précédentes).

2. Évaluer si l'extraction du firmware est techniquement réalisable avec des programmateurs SPI couramment disponibles, tels que :
   - Programneur CH341 (généralement utilisé avec NeoProgrammer)
   - Programneur Xgecu T56 (utilisé avec le logiciel Xgpro)

3. Identifier si l'accès pourrait théoriquement être réalisé :
   - Via pince SOIC8 (sans dessoudage)
   - Via dessoudage de la puce BIOS

4. Rechercher si une documentation publique existe décrivant la suppression du mot de passe par modification du dump firmware pour le modèle d'appareil concerné.

Exemple :
Pour les systèmes HP ProBook, des méthodes documentées existent :
https://gist.github.com/schorschii/752b3a06f7bc3b33ce7b65ff22c27337

5. Documenter :
   - Le niveau d'équipement requis (outils d'entrée de gamme vs professionnels)
   - La disponibilité des techniques publiques
   - La complexité technique
   - L'exposition au risque de l'appareil

## Remédiation
Appliquer une résine époxy sur la puce BIOS/UEFI pour empêcher l'accès physique et le dump ou la réécriture non autorisée du micrologiciel.
