# Évaluer la configuration du démarrage rapide

|ID          |
|------------|
|CHSTG-BOOT-04|

## Résumé

Ce contrôle vise à déterminer si le système utilise un mécanisme de démarrage rapide qui réduit ou ignore des parties du processus d'initialisation standard au démarrage.

## Objectifs du test
- Identifier si le démarrage rapide est activé
- Déterminer si les vérifications au démarrage sont raccourcies
- Évaluer l'impact sur les contrôles de sécurité au démarrage

## Comment tester
1. Arrêter complètement le système.

2. Mettre l'appareil sous tension et observer le comportement au démarrage :
   - Affichage très court de l'écran du micrologiciel
   - Logo de démarrage non visible
   - Transition immédiate vers le chargement du système d'exploitation

3. Tenter d'accéder à la configuration du micrologiciel pendant le démarrage :
   - Si l'accès est difficile ou ignoré, le démarrage rapide peut être activé

4. Si accessible, vérifier la configuration de démarrage du micrologiciel et le paramètre de démarrage rapide.

5. Documenter si le démarrage rapide est activé.

## Remédiation
Désactiver le démarrage rapide dans les paramètres du micrologiciel pour garantir une initialisation complète et permettre aux contrôles de sécurité de fonctionner au démarrage.
