# Évaluer la présence d'un port de débogage SPI

|ID          |
|------------|
|CHSTG-DEBUG-01|

## Résumé

Ce contrôle vise à déterminer si un port de débogage SPI dédié est présent sur la carte mère. L'identification peut être réalisée par analyse des schémas et boardview ou par inspection visuelle directe de la carte mère. L'objectif est d'évaluer l'exposition des interfaces de débogage basées sur SPI.

## Objectifs du test
- Identifier la présence d'une interface de débogage SPI
- Localiser les connecteurs, pastilles ou en-têtes SPI potentiels
- Évaluer le niveau d'exposition de l'accès de débogage SPI

## Comment tester
1. Consulter la documentation disponible :
   - Fichiers de schémas
   - Fichiers boardview

   Identifier les signaux typiquement associés à la communication SPI (ex. CLK, MOSI, MISO, CS).

2. Effectuer une inspection visuelle directe de la carte mère :
   - Rechercher les en-têtes ou pastilles non peuplés
   - Identifier les étiquettes telles que SPI, DEBUG, Jx
   - Localiser les pastilles de test à proximité du contrôleur embarqué, SoC ou composants firmware

Exemple : 
- **Dell Latitude 7280**
![Dell Latitude 7280](img/SPI_port.png)
Sur le Dell Latitude 7280, le port de débogage SPI est clairement identifiable grâce au marquage *JSPI1* sur la carte mère, situé à proximité de la puce BIOS.  

3. Si l'observation des signaux est dans le cadre autorisé, évaluer si l'activité SPI pourrait théoriquement être observée à l'aide de :
   - Systèmes de sondes à ressort (ex. PCBite)
   - Un analyseur logique (ex. Saleae, DSLogic)

4. Documenter :
   - La présence ou l'absence d'une interface de débogage SPI
   - L'emplacement physique
   - Le niveau d'accessibilité
   - Les références documentaires (si identifié via schéma/boardview)

## Remédiation
Non applicable.
