# Vérifier la protection par mot de passe d'accès ATA

|ID          |
|------------|
|CHSTG-BOOT-06|

## Résumé

Ce contrôle vise à déterminer si un mot de passe ATA est configuré pour protéger l'accès au périphérique de stockage pendant le démarrage du système.

## Objectifs du test
- Identifier la présence d'un mot de passe disque ATA
- Confirmer la restriction d'accès au disque avant le chargement du système d'exploitation

## Comment tester
1. S'assurer que le système est arrêté.

2. Mettre l'appareil sous tension.

3. Observer le processus de démarrage :
   - Vérifier la présence d'une demande de mot de passe disque avant le chargement du système d'exploitation
   - Vérifier si l'accès au disque est bloqué jusqu'à la saisie du mot de passe

4. Documenter si un mot de passe ATA est requis.

## Remédiation
Activer un mot de passe disque ATA dans les paramètres du micrologiciel pour restreindre l'accès non autorisé au périphérique de stockage.
