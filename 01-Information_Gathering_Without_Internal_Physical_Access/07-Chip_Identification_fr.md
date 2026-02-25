# Identification des puces

|ID          |
|------------|
|CHSTG-INFO-07|

## Résumé

Ce contrôle vise à identifier les composants internes clés tels que la puce BIOS/UEFI, le contrôleur embarqué et la puce TPM en utilisant la documentation disponible publiquement. L'identification est effectuée à l'aide d'images haute résolution de la carte mère, de fichiers boardview ou de fichiers schématiques sans accès physique à l'appareil.

## Objectifs du test
- Identifier la puce de stockage BIOS/UEFI
- Identifier la puce du contrôleur embarqué
- Identifier la puce TPM
- Déterminer les références et fabricants des puces

## Comment tester
1. Utiliser la référence carte mère identifiée lors du test CHSTG-INFO-01.

2. Collecter la documentation visuelle de la carte mère :
   - Photos haute résolution de revendeurs de pièces détachées
   - Marchés de réparation ou de reconditionnement
   - Forums techniques

3. Si disponible, utiliser les fichiers boardview pour localiser et identifier les composants.

4. Si disponible, utiliser les fichiers schématiques pour confirmer les rôles et références des puces.

5. Recouper les informations entre photos, boardview et schématique pour confirmer l'identification des composants.

6. Documenter les puces identifiées et leurs références pour l'analyse matérielle ultérieure.

## Remédiation
Non applicable.
