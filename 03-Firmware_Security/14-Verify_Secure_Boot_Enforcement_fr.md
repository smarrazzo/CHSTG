# Vérifier l'application du Secure Boot

|ID          |
|------------|
|CHSTG-FIRM-14|

## Résumé

Ce contrôle vise à vérifier si le Secure Boot est correctement activé et appliqué dans la configuration BIOS/UEFI après avoir obtenu l'accès au micrologiciel (ex. via CHSTG-FIRM-01 ou CHSTG-FIRM-06 sans modification du firmware). L'objectif est de s'assurer que le Secure Boot est activé et non configuré en mode enrôlement ou permissif.

## Objectifs du test
- Identifier la présence de la fonctionnalité Secure Boot
- Vérifier si le Secure Boot est activé
- Confirmer que le Secure Boot n'est pas configuré en mode enrôlement
- Évaluer l'application globale des contrôles d'intégrité de démarrage

## Comment tester
1. Accéder à l'interface de configuration BIOS/UEFI (sans modifier le firmware).

2. Naviguer vers la section Secure Boot ou liée à la sécurité.

3. Identifier le statut de configuration du Secure Boot :
   - Secure Boot activé ou désactivé
   - Mode (Standard / Personnalisé / Enrôlement)

4. Vérifier que :
   - Le Secure Boot est activé
   - Le système n'est pas en mode enrôlement
   - Les clés Secure Boot sont correctement installées

5. Documenter le statut du Secure Boot et le mode de configuration.

## Remédiation
Activer le Secure Boot en mode application standard et s'assurer que le système n'est pas configuré en mode enrôlement ou permissif.
