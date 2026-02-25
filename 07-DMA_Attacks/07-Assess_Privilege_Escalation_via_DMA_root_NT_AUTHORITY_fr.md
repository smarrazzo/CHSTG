# Évaluer l'élévation de privilèges via DMA (root / NT AUTHORITY)

|ID          |
|------------|
|CHSTG-DMA-07|

## Résumé

Ce contrôle se concentre sur la phase finale d'une attaque basée sur le DMA : obtenir un contrôle administratif complet sur le système d'exploitation cible. En utilisant une injection en mode noyau existante (établie dans CHSTG-DMA-06), un attaquant peut contourner tous les mécanismes d'authentification et d'autorisation standard. Cela conduit à l'exécution de commandes arbitraires en tant que **NT AUTHORITY\SYSTEM** sous Windows ou **root** sous Linux, représentant un compromis total de l'intégrité et de la confidentialité du système.

## Objectifs du test
- Démontrer le passage de l'accès mémoire brut aux privilèges administratifs complets au niveau du système d'exploitation.
- Confirmer que les frontières de sécurité entre l'espace utilisateur et l'espace noyau peuvent être entièrement neutralisées via le DMA.
- Vérifier la capacité de lancer des shells interactifs privilégiés ou d'exécuter des commandes au niveau root sans interaction utilisateur.

## Comment tester
Ce test est réalisé sur un système en fonctionnement avec des ports PCIe/Thunderbolt externes ou facilement accessibles. Il ne nécessite pas de démontage interne de l'appareil.

### Prérequis
- Une connexion DMA réussie doit être établie.
- Un module noyau (KMD) doit déjà être chargé dans la RAM de la cible (voir **CHSTG-DMA-06**).
- L'adresse mémoire du module noyau chargé doit être connue (ex. `0x7ffff000`).

### Exécution logicielle
En utilisant **PCILeech**, exécuter les commandes suivantes selon le système d'exploitation cible :

1.  **Pour Windows (élévation vers SYSTEM) :**
    Ouvrir une invite de commandes privilégiée sur la machine de l'attaquant et exécuter :
    `pcileech wx64_pscmd -kmd 0x7ffff000`
    - **Critère de succès :** Une invite de commandes interactive est lancée sur le système cible avec les privilèges **NT AUTHORITY\SYSTEM**.

2.  **Pour Linux (élévation vers root) :**
    Exécuter la commande suivante pour exécuter des tâches arbitraires avec les privilèges root :
    `pcileech wx64_exec_root -kmd 0x7ffff000`
    - **Critère de succès :** Les commandes sont exécutées avec succès avec un UID de 0 (root).

## Remédiation
- **Niveau BIOS/UEFI :** Activer **Intel VT-d** ou **AMD-Vi** (IOMMU) pour appliquer l'isolation mémoire au niveau matériel, ce qui empêche les périphériques d'accéder à des régions mémoire non autorisées.
- **Niveau système d'exploitation :** Activer la **protection DMA du noyau** (ex. Windows 10/11) pour s'assurer que le système d'exploitation restreint le DMA pour les périphériques PCIe non de confiance ou nouvellement connectés jusqu'au déverrouillage du système.
- **Intégrité mémoire :** Activer des fonctionnalités telles que **Hypervisor-Protected Code Integrity (HVCI)** pour empêcher l'injection de code malveillant dans le noyau même si l'accès mémoire est obtenu.
