# Évaluer la présence d'un port de débogage UART

|ID          |
|------------|
|CHSTG-DEBUG-02|

## Résumé

Ce contrôle vise à déterminer si un port de débogage UART dédié est présent sur la carte mère. L'identification peut être réalisée par analyse des schémas et boardview ou par inspection visuelle directe de la carte mère. L'objectif est d'évaluer l'exposition des interfaces de débogage basées sur UART.

## Objectifs du test
- Identifier la présence d'une interface de débogage UART
- Localiser les en-têtes, pastilles ou connecteurs UART potentiels
- Évaluer le niveau d'exposition de l'accès de débogage série

## Comment tester
1. Consulter la documentation disponible :
   - Fichiers de schémas
   - Fichiers boardview

   Identifier les signaux typiquement associés à la communication UART (ex. TX, RX, GND, VCC).

2. Effectuer une inspection visuelle directe de la carte mère :
   - Rechercher les en-têtes ou pastilles non peuplés
   - Identifier les étiquettes telles que UART, TX, RX, DEBUG, CONSOLE, connecteurs Jx
   - Localiser les pastilles de test à proximité du contrôleur embarqué, SoC ou composants firmware

Exemple : 
- **Dell Latitude 7280**
![Dell Latitude 7280](img/UART_port.png)
Sur le Dell Latitude 7280, le port de débogage UART est clairement identifiable grâce au marquage *JUART1* sur la carte mère.

3. Si l'observation des signaux est dans le cadre autorisé, évaluer si l'activité de communication série pourrait être observée à l'aide de :
   - Systèmes de sondes à ressort (ex. PCBite)
   - Un analyseur logique (ex. Saleae, DSLogic)

4. Documenter :
   - La présence ou l'absence d'une interface de débogage UART
   - L'emplacement physique
   - Le niveau d'accessibilité
   - Les références documentaires (si identifié via schéma/boardview)

## Remédiation
Non applicable.
