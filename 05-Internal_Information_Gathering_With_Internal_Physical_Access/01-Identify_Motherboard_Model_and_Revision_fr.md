# Identifier le modèle et la révision de la carte mère

|ID          |
|------------|
|CHSTG-INT-01|

## Résumé

Ce contrôle vise à identifier le modèle exact de la carte mère et la révision matérielle après démontage de l'appareil. L'objectif est de collecter les identifiants spécifiques à la carte mère et de les mettre en relation avec les informations préalablement recueillies lors de CHSTG-INFO-01.

## Objectifs du test
- Identifier les marquages de modèle et de révision de la carte mère
- Comparer les constatations internes avec les résultats d'identification externe
- Affiner la collecte d'informations OSINT à l'aide des identifiants internes

## Comment tester
1. Démonter l'appareil selon les procédures standard.

2. Localiser les marquages d'identification de la carte mère, tels que :
   - Référence du modèle de carte imprimée
   - Numéro de révision du PCB
   - Numéro de série
   - Code fabricant

3. Noter tous les identifiants exactement tels qu'inscrits sur la carte mère.

4. Comparer les informations collectées avec les résultats obtenus lors de CHSTG-INFO-01.

5. Si de nouveaux identifiants ou des identifiants plus précis sont trouvés, répéter la phase de collecte d'informations OSINT en utilisant :
   - La référence de la carte mère
   - Le numéro de révision du PCB
   - Les numéros de pièces internes

6. Documenter toute divergence ou nouvelle révision matérielle identifiée.

## Remédiation
Non applicable.
