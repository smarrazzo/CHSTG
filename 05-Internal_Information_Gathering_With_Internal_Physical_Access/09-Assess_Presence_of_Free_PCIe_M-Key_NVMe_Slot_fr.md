# Évaluer la présence d'un emplacement PCIe M-Key (NVMe) libre

|ID          |
|------------|
|CHSTG-INT-09|

## Résumé

Ce contrôle vise à déterminer si un emplacement PCIe M-Key (NVMe) libre est présent sur la carte mère. L'objectif est d'identifier la disponibilité d'une interface d'extension de stockage interne haute vitesse inutilisée.

## Objectifs du test
- Identifier la présence d'un emplacement PCIe M-Key (NVMe)
- Déterminer si l'emplacement est occupé ou libre
- Évaluer la disponibilité des capacités d'extension NVMe internes

## Comment tester
1. Ouvrir l'appareil selon les procédures de démontage standard.

2. Inspecter visuellement la carte mère pour les emplacements M.2.

3. Identifier si un emplacement PCIe M-Key (NVMe) est présent.

4. Déterminer si :
   - L'emplacement est occupé par un dispositif de stockage NVMe
   - L'emplacement est présent mais inutilisé (libre)

5. Documenter la présence et le statut (occupé ou libre) de l'emplacement PCIe M-Key (NVMe).

## Remédiation
Non applicable.
