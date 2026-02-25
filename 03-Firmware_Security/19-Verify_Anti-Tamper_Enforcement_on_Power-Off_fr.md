# Vérifier l'application de l'anti-effraction à l'arrêt

|ID          |
|------------|
|CHSTG-FIRM-19|

## Résumé

Ce contrôle vise à vérifier si le micrologiciel est configuré pour couper automatiquement l'alimentation du système lors de la détection d'ouverture du châssis après avoir obtenu l'accès BIOS/UEFI (ex. via CHSTG-FIRM-01 ou CHSTG-FIRM-06 sans modification du firmware). L'objectif est de déterminer si des mécanismes d'application actifs sont configurés en réponse à la détection d'intrusion physique.

## Objectifs du test
- Identifier la présence de mécanismes d'arrêt automatique déclenchés par l'intrusion du châssis
- Vérifier si l'application de l'arrêt est activée
- Confirmer la configuration de la réponse du firmware à la détection d'effraction

## Comment tester
1. Accéder à l'interface de configuration BIOS/UEFI (sans modifier le firmware).

2. Naviguer vers les sections sécurité ou liées à l'anti-effraction.

3. Identifier les options de configuration telles que :
   - Arrêt à l'ouverture du capot

4. Vérifier si ces mécanismes sont :
   - Présents
   - Activés
   - Configurables

5. Documenter le statut d'application et la configuration.

## Remédiation
Activer l'arrêt automatique ou l'application de l'arrêt lors de la détection d'intrusion du châssis dans les paramètres BIOS/UEFI.
