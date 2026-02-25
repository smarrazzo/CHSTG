# Évaluer la présence d'un port de débogage JTAG

|ID          |
|------------|
|CHSTG-DEBUG-03|

## Résumé

Ce contrôle vise à déterminer si un port de débogage JTAG dédié est présent sur la carte mère. L'identification peut être réalisée par analyse des schémas et boardview ou par inspection visuelle directe de la carte mère. L'objectif est d'évaluer l'exposition des interfaces de débogage basées sur JTAG.

## Objectifs du test
- Identifier la présence d'une interface de débogage JTAG
- Localiser les en-têtes, pastilles ou connecteurs JTAG potentiels
- Évaluer le niveau d'exposition de l'accès de débogage matériel

## Comment tester
1. Consulter la documentation disponible :
   - Fichiers de schémas
   - Fichiers boardview

   Identifier les signaux typiquement associés à la communication JTAG (ex. TCK, TMS, TDI, TDO, TRST).

2. Effectuer une inspection visuelle directe de la carte mère :
   - Rechercher les en-têtes ou pastilles de test non peuplés
   - Identifier les étiquettes telles que JTAG, DEBUG, JTCK, JTMS ou similaires
   - Localiser les connecteurs à proximité du processeur principal, chipset ou contrôleur embarqué

Exemple :
- **HP Probook 430 G6**
![HP Probook 430 G6](img/JTAG_port.png)
Sur le HP Probook 430 G6, le port de débogage JTAG est clairement identifiable grâce à l'analyse du fichier Boardview, qui permet de localiser précisément les signaux et connecteurs associés.

3. Si l'observation des signaux est dans le cadre autorisé, évaluer si l'activité JTAG pourrait théoriquement être observée à l'aide de :
   - Systèmes de sondes à ressort (ex. PCBite)
   - Un analyseur logique (ex. Saleae, DSLogic)

4. Documenter :
   - La présence ou l'absence d'une interface de débogage JTAG
   - L'emplacement physique
   - Le niveau d'accessibilité
   - Les références documentaires (si identifié via schéma/boardview)

## Remédiation
Non applicable.
