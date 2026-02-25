# Évaluer la suppression du mot de passe via image firmware déverrouillée

|ID          |
|------------|
|CHSTG-FIRM-07|

## Résumé

Ce contrôle vise à évaluer si la protection par mot de passe BIOS/UEFI peut être contournée en flashant une image firmware déverrouillée préalablement identifiée lors de CHSTG-INFO-06. L'objectif est d'évaluer l'exposition de l'appareil aux attaques par remplacement de micrologiciel lorsque l'accès physique est disponible.

## Objectifs du test
- Déterminer si des images firmware déverrouillées existent pour le modèle d'appareil
- Évaluer la faisabilité du flashage d'une image firmware alternative
- Identifier l'équipement requis pour la réécriture du micrologiciel
- Évaluer le risque global de contournement du mot de passe par remplacement du firmware

## Comment tester
1. Confirmer qu'une image firmware déverrouillée ou modifiée a été identifiée lors de CHSTG-INFO-06.

2. Identifier la référence de la puce de stockage BIOS/UEFI (à partir des étapes d'identification précédentes).

3. Évaluer si la réécriture du firmware serait techniquement réalisable avec des programmateurs SPI couramment disponibles, tels que :
   - Programneur CH341 (généralement utilisé avec NeoProgrammer)
   - Programneur Xgecu T56 (utilisé avec le logiciel Xgpro)

4. Identifier si l'accès physique à la puce firmware permettrait théoriquement :
   - Un accès en circuit via pince SOIC8 (sans dessoudage)
   - Un accès direct à la puce après dessoudage

5. Documenter :
   - La disponibilité des images firmware déverrouillées
   - Le niveau d'équipement requis (outils d'entrée de gamme vs professionnels)
   - La complexité technique
   - Les risques liés au remplacement du firmware (incompatibilité matérielle, corruption du firmware)
   - L'exposition globale de l'appareil aux attaques par remplacement du firmware

## Remédiation
Appliquer une résine époxy sur la puce BIOS/UEFI pour empêcher l'accès physique et la réécriture non autorisée du micrologiciel.
