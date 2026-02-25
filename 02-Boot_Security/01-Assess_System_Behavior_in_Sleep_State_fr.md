# Évaluer le comportement du système en veille

|ID          |
|------------|
|CHSTG-BOOT-01|

## Résumé

Ce contrôle vise à déterminer si le système est actuellement en état de veille en observant son comportement tout en ayant un accès direct à l'appareil.

## Objectifs du test
- Identifier si le système est en mode veille
- Différencier l'état de veille de l'état arrêté

## Comment tester
1. Observer les indicateurs de l'appareil :
   - Comportement de la LED d'alimentation (clignotement ou état basse consommation fixe)
   - État de l'écran
   - Activité du ventilateur
   - LEDs des périphériques (clavier, réseau, etc.)

2. Interagir avec le système :
   - Appuyer sur une touche du clavier
   - Bouger la souris ou le pavé tactile
   - Appuyer brièvement sur le bouton d'alimentation

3. Déterminer l'état du système :
   - Si le système reprend rapidement → état de veille
   - Si une séquence de démarrage complète démarre → état arrêté

4. Documenter le comportement observé.

## Remédiation
Désactiver le mode veille ou exiger une authentification au réveil dans les paramètres de gestion de l'alimentation pour empêcher l'accès non autorisé à une session active.
