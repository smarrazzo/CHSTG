# Évaluer les options de démarrage alternatives (CD/DVD, USB)

|ID          |
|------------|
|CHSTG-BOOT-07|

## Résumé

Ce contrôle vise à déterminer si le système permet le démarrage depuis des périphériques alternatifs tels que CD/DVD ou USB au démarrage.

## Objectifs du test
- Identifier la disponibilité des périphériques de démarrage alternatifs
- Déterminer si l'utilisateur peut sélectionner une autre source de démarrage
- Évaluer l'application des restrictions de démarrage

## Comment tester
1. Mettre l'appareil sous tension.

2. Accéder au menu de sélection de démarrage (touche du menu de démarrage au démarrage).

3. Observer les options de démarrage disponibles :
   - Stockage interne
   - Périphériques USB
   - Périphériques CD/DVD

4. Tenter de sélectionner un périphérique de démarrage alternatif.

5. Documenter si le démarrage alternatif est autorisé ou restreint.

## Remédiation
Restreindre les périphériques de démarrage alternatifs dans les paramètres du micrologiciel et protéger la configuration de démarrage avec un mot de passe administrateur.
