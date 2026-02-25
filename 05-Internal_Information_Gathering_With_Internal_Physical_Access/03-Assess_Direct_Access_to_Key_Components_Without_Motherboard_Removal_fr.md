# Évaluer l'accès direct aux composants clés sans retrait de la carte mère

|ID          |
|------------|
|CHSTG-INT-03|

## Résumé

Ce contrôle vise à déterminer si les composants clés permettant des attaques matérielles sont directement accessibles après avoir retiré uniquement le capot de l'appareil, sans nécessiter le retrait complet de la carte mère. L'objectif est d'évaluer le niveau de protection offert par la disposition interne de l'appareil.

## Objectifs du test
- Identifier l'accessibilité des composants pertinents pour la sécurité
- Déterminer si le retrait de la carte mère est requis pour l'accès
- Évaluer l'exposition des composants critiques après un démontage minimal

## Comment tester
1. Retirer uniquement le capot externe de l'appareil (sans retirer la carte mère).

2. Inspecter visuellement la disposition interne.

3. Identifier si les composants suivants sont directement accessibles :
   - Puce TPM
   - Puce BIOS/UEFI
   - Contrôleur embarqué (EC)
   - Emplacements PCIe ou périphériques connectés PCIe accessibles

4. Déterminer si l'accès à ces composants nécessite :
   - Aucun démontage supplémentaire
   - Un retrait partiel du blindage
   - Un retrait complet de la carte mère

5. Documenter le niveau d'accessibilité pour chaque composant.

## Remédiation
Non applicable.
