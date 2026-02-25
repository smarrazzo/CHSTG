# Évaluer la faisabilité d'attaque DMA via PCIe NVMe (M-Key)

|ID          |
|------------|
|CHSTG-DMA-02|

## Résumé

Ce contrôle évalue le risque d'attaques d'accès direct à la mémoire (DMA) via l'emplacement M.2 NVMe (M-Key). Bien que généralement internes, ces emplacements sont souvent accessibles via des trappes de maintenance ou lors de scénarios d'accès physique rapide. Comme les disques NVMe communiquent directement sur le bus PCIe, un attaquant peut remplacer le disque de stockage par un périphérique malveillant capable de DMA pour lire ou écrire la mémoire système. Cette attaque est réalisée en « cold-plug » du dispositif alors que le système est arrêté puis en démarrant le système d'exploitation.

## Objectifs du test
- Vérifier si l'emplacement M.2 NVMe du système permet un accès DMA non autorisé à la mémoire système.
- Déterminer si des données sensibles (ex. dumps RAM) peuvent être extraites via l'interface M-Key.
- Évaluer l'efficacité des protections DMA au niveau système lorsqu'un périphérique malveillant est présent au démarrage.

## Comment tester
Ce test se concentre sur les scénarios où le port NVMe est accessible (ex. via un panneau d'accès facile) sans démontage complet du système.

### Prérequis
- S'assurer que les protections anti-DMA identifiées dans le nœud **Sécurité du micrologiciel** (telles qu'IOMMU ou VT-d) sont désactivées pour établir une base de référence pour l'attaque.

### Configuration matérielle
1.  **Alimentation cible :** S'assurer que le système cible est complètement **arrêté**.
2.  **Dispositif malveillant :** Utiliser une carte DMA à base FPGA, telle que **PCIeSquirrel**.
3.  **Adaptateur :** Connecter la carte DMA au système à l'aide d'un **adaptateur PCIe-1x vers M.2 M-Key**.
4.  **Connexion :** Insérer l'ensemble adaptateur/carte dans l'emplacement NVMe du système cible.

### Exécution logicielle
1.  **Mise sous tension :** Mettre le système cible sous tension et le laisser démarrer complètement dans le système d'exploitation.
2.  **Vérifier l'accès en lecture :** Sur la machine de l'attaquant (connectée à la carte DMA), utiliser **PCILeech** pour vérifier si la RAM peut être lue :
    `pcileech testmemread`
3.  **Vérifier l'accès en écriture :** Vérifier les capacités de lecture/écriture aléatoire :
    `pcileech testmemrandwrite`

## Remédiation
- **Niveau Firmware/BIOS :** Activer les fonctionnalités d'isolation mémoire au niveau matériel, telles que **Intel VT-d** ou **AMD-Vi** (IOMMU), pour empêcher les périphériques d'accéder à des régions mémoire non autorisées.
- **Niveau système d'exploitation :** Activer la **protection DMA du noyau** (ex. sous Windows 10/11) pour s'assurer que le système d'exploitation gère et restreint le DMA pour tous les périphériques PCIe.
- **Sécurité physique :** Utiliser des scellés inviolables ou des vis spécialisées sur les trappes de maintenance pour détecter ou empêcher l'accès non autorisé aux emplacements M.2 internes.
