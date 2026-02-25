# Identifier la présence du TPM

|ID          |
|------------|
|CHSTG-INT-14|

## Résumé

Ce contrôle vise à identifier la présence d'un module de plateforme sécurisée (TPM) sur la carte mère, à déterminer son emplacement physique exact et à noter sa référence de composant précise. L'objectif est de documenter l'implémentation du TPM pour une analyse matérielle ultérieure.

## Objectifs du test
- Identifier la présence d'une puce TPM
- Déterminer l'emplacement physique exact sur la carte mère
- Noter la référence fabricant et modèle

## Comment tester
1. Ouvrir l'appareil selon les procédures de démontage standard.

2. Inspecter visuellement la carte mère pour une puce TPM dédiée.

3. Identifier :
   - Le marquage de la puce (fabricant et modèle)
   - Le type de boîtier
   - L'emplacement exact sur la carte

4. Si nécessaire, mettre en relation avec les étiquettes sérigraphiées de la carte ou les informations schéma/boardview pour confirmer l'identification.

5. Documenter :
   - La présence du TPM (Oui / Non)
   - La référence exacte de la puce
   - L'emplacement physique sur la carte mère

## Remédiation
Appliquer une résine époxy sur les composants sensibles tels que la puce TPM pour empêcher l'effraction physique.
