# Vérifier la protection du vidage TPM via anti-effraction

|ID          |
|------------|
|CHSTG-FIRM-20|

## Résumé

Ce contrôle vise à vérifier si le micrologiciel est configuré pour vider automatiquement le TPM lors de la détection d'ouverture du châssis après avoir obtenu l'accès BIOS/UEFI (ex. via CHSTG-FIRM-01 ou CHSTG-FIRM-06 sans modification du firmware). L'objectif est de déterminer si un événement d'effraction déclenche l'invalidation des données TPM comme mesure de protection.

## Objectifs du test
- Identifier la présence d'un mécanisme de vidage TPM lié à la détection d'intrusion du châssis
- Vérifier si le vidage automatique du TPM est activé
- Confirmer la configuration au niveau firmware de la protection TPM déclenchée par effraction

## Comment tester
1. Accéder à l'interface de configuration BIOS/UEFI (sans modifier le firmware).

2. Naviguer vers les sections sécurité, TPM ou liées à l'anti-effraction.

3. Identifier les options de configuration telles que :
   - Vider le TPM au démarrage après ouverture du capot
   
4. Vérifier si ces mécanismes sont :
   - Présents
   - Activés
   - Configurables

5. Documenter le statut de configuration et le comportement de protection.

## Remédiation
Activer le vidage du TPM lors de la détection d'intrusion du châssis dans les paramètres BIOS/UEFI pour protéger le matériel cryptographique contre l'effraction physique.
