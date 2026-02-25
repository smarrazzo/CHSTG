# Évaluer les attaques DMA via les autres emplacements PCIe (A, B, E Key)

|ID          |
|------------|
|CHSTG-DMA-03|

## Résumé

De nombreux ordinateurs portables et de bureau modernes contiennent des emplacements M.2 internes pour des modules d'extension tels que WiFi, Bluetooth (clés A ou E) ou cellulaire/WWAN (clé B). Ces emplacements sont souvent câblés directement sur le bus PCIe. Ce contrôle évalue si ces interfaces PCIe secondaires peuvent être exploitées pour réaliser des attaques d'accès direct à la mémoire (DMA). En remplaçant un module interne par un dispositif FPGA malveillant à l'aide d'une chaîne d'adaptateurs, un attaquant peut potentiellement contourner les frontières de sécurité du système d'exploitation pour lire ou modifier la mémoire système.

## Objectifs du test
- Déterminer si les emplacements PCIe non dédiés au stockage (clés A, B ou E) sont soumis à des politiques de protection DMA.
- Vérifier la capacité d'exécuter des lectures ou écritures mémoire non autorisées via ces interfaces spécifiques.
- Évaluer si le firmware ou le système d'exploitation isole efficacement ces périphériques à l'aide d'IOMMU/VT-d.

## Comment tester
Ce test cible les emplacements internes accessibles via des panneaux de maintenance ou des capots facilement amovibles sans démontage complet du système.

### Prérequis
- S'assurer que les protections anti-DMA (ex. IOMMU, VT-d) identifiées lors de l'évaluation **Sécurité du micrologiciel** sont désactivées pour établir une base de référence, ou les laisser activées pour tester leur efficacité.

### Configuration matérielle
1.  **Alimentation cible :** S'assurer que le système cible est complètement **arrêté**.
2.  **Dispositif malveillant :** Préparer une carte DMA à base FPGA, telle que **PCIeSquirrel**.
3.  **Chaîne d'adaptateurs :** Connecter le matériel dans l'ordre suivant pour relier les différents types d'emplacements :
    * **PCIeSquirrel** (PCIe-1x) -> **Adaptateur PCIe-1x vers M.2 M-Key** -> **Adaptateur M-Key vers [A, B ou E] Key**.
4.  **Connexion :** Retirer le module existant (ex. carte WiFi) et insérer la chaîne d'adaptateurs dans l'emplacement cible.

### Exécution logicielle
1.  **Mise sous tension :** Démarrer le système cible et attendre le chargement complet du système d'exploitation.
2.  **Vérifier l'accès en lecture :** Sur la machine de l'attaquant, utiliser **PCILeech** pour vérifier les capacités de lecture mémoire :
    `pcileech testmemread`
3.  **Vérifier l'accès en écriture :** Utiliser la commande suivante pour vérifier les capacités d'écriture mémoire :
    `pcileech testmemrandwrite`

## Remédiation
- **Niveau Firmware/BIOS :** Activer **Intel VT-d** ou **AMD-Vi** (IOMMU) pour appliquer l'isolation mémoire pour tous les périphériques PCIe, y compris ceux des emplacements d'extension M.2.
- **Niveau système d'exploitation :** Activer la **protection DMA du noyau** pour s'assurer que le système d'exploitation gère l'accès mémoire des périphériques et empêche le DMA pour les dispositifs non autorisés ou non de confiance.
- **Sécurité physique :** S'assurer que les emplacements d'extension internes ne sont pas facilement accessibles en utilisant des étiquettes inviolables ou des vis de sécurité sur les panneaux d'accès.
