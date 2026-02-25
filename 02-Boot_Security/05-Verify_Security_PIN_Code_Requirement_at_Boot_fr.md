# Vérifier l'exigence de code PIN de sécurité au démarrage

|ID          |
|------------|
|CHSTG-BOOT-05|

## Résumé

Ce contrôle vise à déterminer si un code PIN de sécurité est requis pendant le démarrage du système avant le chargement du système d'exploitation.

## Objectifs du test
- Identifier la présence d'un code PIN de sécurité au démarrage
- Confirmer l'exigence d'une interaction utilisateur avant le démarrage du système

## Comment tester
1. S'assurer que le système est arrêté.

2. Mettre l'appareil sous tension.

3. Observer le processus de démarrage :
   - Vérifier la présence d'une demande de PIN pré-démarrage
   - Vérifier si le système bloque le démarrage jusqu'à la saisie du PIN

4. Documenter si un PIN de démarrage est requis.

## Remédiation
Activer un code PIN de sécurité au démarrage dans la configuration du micrologiciel ou du chiffrement du disque pour empêcher le démarrage non autorisé du système.
