# Évaluer l'injection de code au niveau noyau via DMA

|ID          |
|------------|
|CHSTG-DMA-06|

## Résumé

Une fois les capacités de lecture/écriture par accès direct à la mémoire (DMA) confirmées, un attaquant peut contourner les frontières de sécurité du système d'exploitation (OS) en injectant du code directement dans le noyau. Cette attaque permet l'exécution de code non signé avec les privilèges les plus élevés sans interagir avec l'écran de connexion du système d'exploitation ni avoir besoin d'identifiants locaux. Ce contrôle évalue le risque d'une prise de contrôle complète du système (ex. obtention d'un shell SYSTEM sous Windows ou accès root sous Linux) via les ports externes ou internes basés sur PCIe.

## Objectifs du test
- Démontrer la capacité d'injecter et de charger un pilote en mode noyau (KMD) malveillant dans la mémoire système.

## Comment tester
Ce test doit être effectué sur un système en fonctionnement avec une connexion DMA établie (via Thunderbolt ou emplacements PCIe) sans démontage complet de l'appareil.

### Prérequis
- Une connexion DMA lecture/écriture réussie vérifiée par `pcileech testmemread` et `pcileech testmemrandwrite`.
- Les protections anti-DMA dans le BIOS et le noyau doivent être désactivées pour confirmer la vulnérabilité.

### Exécution logicielle
Utiliser **PCILeech** pour réaliser l'injection noyau :

1.  **Charger le module noyau :** Exécuter la commande appropriée pour le système d'exploitation cible afin de charger le Kernel Memory Device (KMD) en RAM :
    * **Windows 11 :** `pcileech kmdload -kmd WIN11_X64`
    * **Linux :** `pcileech kmdload -kmd LINUX_X64_48`
2.  **Capturer l'adresse mémoire :** En cas de succès, la commande renverra une adresse mémoire spécifique (ex. `0x7ffff000`). Cette adresse est requise pour les commandes suivantes.

## Remédiation
- **Niveau Firmware/BIOS :** Activer **Intel VT-d** ou **AMD-Vi** (IOMMU) pour appliquer une isolation mémoire stricte au niveau matériel.
- **Niveau système d'exploitation :** Activer la **protection DMA du noyau** pour empêcher le système d'exploitation d'autoriser le DMA pour les dispositifs non autorisés ou non de confiance.
- **Configuration :** S'assurer que le système d'exploitation est configuré pour bloquer les pilotes non signés et que le Secure Boot est appliqué pour protéger l'intégrité de la chaîne de démarrage.
