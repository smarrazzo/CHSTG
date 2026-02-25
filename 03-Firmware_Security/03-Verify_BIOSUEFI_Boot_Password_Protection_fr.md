# Vérifier la protection par mot de passe de démarrage BIOS/UEFI

|ID          |
|------------|
|CHSTG-FIRM-03|

## Résumé

Ce contrôle vise à déterminer si un mot de passe de démarrage BIOS/UEFI est requis au démarrage du système avant que le système d'exploitation ne commence à se charger.

## Objectifs du test
- Identifier la présence d'un mot de passe de démarrage BIOS/UEFI
- Vérifier l'exigence d'authentification au démarrage du système
- Confirmer la protection contre le démarrage non autorisé du système

## Comment tester
1. S'assurer que le système est arrêté.

2. Mettre l'appareil sous tension.

3. Observer le processus de démarrage :
   - Vérifier si une demande de mot de passe apparaît avant le chargement du système d'exploitation
   - Vérifier si le système bloque la poursuite du démarrage tant que le mot de passe n'est pas saisi

4. Documenter si un mot de passe de démarrage BIOS/UEFI est requis.

## Remédiation
Configurer un mot de passe de démarrage BIOS/UEFI pour empêcher le démarrage non autorisé du système.
