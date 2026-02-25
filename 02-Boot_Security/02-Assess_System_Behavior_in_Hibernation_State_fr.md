# Évaluer le comportement du système en hibernation

|ID          |
|------------|
|CHSTG-BOOT-02|

## Résumé

Ce contrôle vise à déterminer si le système est actuellement en état d'hibernation en observant son comportement tout en ayant un accès direct à l'appareil.

## Objectifs du test
- Identifier si le système est en mode hibernation
- Différencier l'état d'hibernation des états veille et arrêté

## Comment tester
1. Observer les indicateurs de l'appareil :
   - LED d'alimentation typiquement éteinte
   - Écran éteint
   - Aucune activité du ventilateur
   - Aucune activité des LEDs des périphériques

2. Appuyer une fois sur le bouton d'alimentation.

3. Déterminer le comportement du système :
   - Si le système restaure la session précédente après un temps de démarrage plus long → état d'hibernation
   - Si le système effectue un démarrage à froid → état arrêté
   - Si le système reprend instantanément → état de veille

4. Documenter le comportement observé.

## Remédiation
Désactiver le mode hibernation dans les paramètres de gestion de l'alimentation lorsqu'il n'est pas requis, afin d'empêcher la récupération de données sensibles depuis le disque.
