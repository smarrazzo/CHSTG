# Évaluer l'accessibilité du démarrage réseau

|ID          |
|------------|
|CHSTG-BOOT-08|

## Résumé

Ce contrôle vise à déterminer si le système permet le démarrage depuis le réseau au démarrage.

## Objectifs du test
- Identifier la disponibilité de l'option de démarrage réseau
- Déterminer si l'utilisateur peut initier un démarrage réseau
- Évaluer l'application des restrictions de démarrage

## Comment tester
1. Mettre l'appareil sous tension.

2. Accéder au menu de sélection de démarrage (touche du menu de démarrage au démarrage).

3. Observer les options de démarrage disponibles :
   - Démarrage réseau (PXE)

4. Tenter de sélectionner l'option de démarrage réseau.

5. Documenter si le démarrage réseau est autorisé ou restreint.

## Remédiation
Désactiver le démarrage réseau dans les paramètres du micrologiciel et protéger la configuration de démarrage avec un mot de passe administrateur.
