# Vérifier l'activation du mécanisme anti-effraction

|ID          |
|------------|
|CHSTG-FIRM-18|

## Résumé

Ce contrôle vise à vérifier si les mécanismes anti-effraction au niveau firmware, tels que la détection d'ouverture du châssis, sont activés après avoir obtenu l'accès BIOS/UEFI (ex. via CHSTG-FIRM-01 ou CHSTG-FIRM-06 sans modification du firmware). L'objectif est de déterminer si le système détecte et enregistre les événements d'intrusion physique.

## Objectifs du test
- Identifier la présence de mécanismes de détection d'intrusion du châssis
- Vérifier si les fonctionnalités anti-effraction sont activées
- Confirmer si les événements d'intrusion sont enregistrés ou signalés

## Comment tester
1. Accéder à l'interface de configuration BIOS/UEFI (sans modifier le firmware).

2. Naviguer vers les sections sécurité ou surveillance matérielle.

3. Identifier les options de configuration liées aux mécanismes anti-effraction, telles que :
   - Capteur d'ouverture de capot
   - Détection d'intrusion du châssis
   - Détection d'effraction sur appareil firmware

4. Vérifier si ces mécanismes sont :
   - Présents
   - Activés
   - Configurables

5. Si l'interface firmware le prend en charge, vérifier si les événements d'intrusion sont enregistrés ou indiqués.

6. Documenter le statut d'activation et la configuration.

## Remédiation
Activer tous les mécanismes anti-effraction et de détection d'intrusion du châssis disponibles dans les paramètres BIOS/UEFI pour s'assurer que les tentatives d'accès physique sont détectées et enregistrées.
