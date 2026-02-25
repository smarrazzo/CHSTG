# Évaluer la présence d'autres interfaces de débogage

|ID          |
|------------|
|CHSTG-DEBUG-04|

## Résumé

Ce contrôle vise à déterminer si des interfaces de débogage supplémentaires sont présentes sur la carte mère au-delà de SPI, UART ou JTAG. L'identification peut être réalisée par analyse des schémas et boardview ou par inspection visuelle directe. L'objectif est d'évaluer l'exposition globale des interfaces de débogage au niveau matériel.

## Objectifs du test
- Identifier la présence d'interfaces de débogage supplémentaires
- Localiser les en-têtes, pastilles ou connecteurs liés au débogage
- Évaluer le niveau d'exposition des points d'accès de débogage non documentés ou secondaires

## Comment tester
1. Consulter la documentation disponible :
   - Fichiers de schémas
   - Fichiers boardview

   Identifier les connecteurs ou signaux associés à des protocoles de débogage alternatifs (ex. SWD, débogage eSPI, en-têtes de débogage spécifiques au fabricant).

2. Effectuer une inspection visuelle directe de la carte mère :
   - Rechercher les en-têtes à broches ou groupes de pastilles de test non peuplés
   - Identifier les étiquettes sérigraphiées telles que DEBUG, TEST, SWD, CNx, Jx
   - Inspecter les zones à proximité du SoC, EC, chipset ou composants de sécurité

3. Si l'observation des signaux est dans le cadre autorisé, évaluer si l'activité pourrait théoriquement être observée à l'aide de :
   - Systèmes de sondes à ressort (ex. PCBite)
   - Un analyseur logique (ex. Saleae, DSLogic)

4. Documenter :
   - La présence ou l'absence d'interfaces de débogage supplémentaires
   - L'emplacement physique
   - Le niveau d'accessibilité
   - Les références documentaires (si identifié via schéma/boardview)

## Remédiation
Non applicable.
