# Évaluer la faisabilité d'un dump RAM complet via DMA

|ID          |
|------------|
|CHSTG-DMA-05|

## Résumé

Une fois l'accès direct à la mémoire (DMA) établi avec succès via un port externe ou interne (comme testé dans CHSTG-DMA-01 à CHSTG-DMA-03), l'étape critique suivante consiste à évaluer la capacité de réaliser une acquisition forensique complète de la mémoire volatile du système. Un dump RAM complet permet à un attaquant d'effectuer une analyse hors ligne pour extraire des informations sensibles telles que les clés de chiffrement (BitLocker, LUKS), les identifiants utilisateur et les jetons de session actifs. Ce contrôle se concentre sur l'exécution technique d'un dump mémoire à l'aide de matériel et logiciels spécialisés.

## Objectifs du test
- Vérifier la capacité de contourner les protections mémoire au niveau du système d'exploitation pour lire l'intégralité de l'espace d'adressage physique.
- Acquérir avec succès une image forensique de la RAM pour analyse hors ligne.
- Confirmer que la taille du dump acquis correspond à la capacité RAM physique du système cible.

## Comment tester
Ce test suppose qu'une configuration matérielle réussie a déjà été établie avec un dispositif capable de DMA (ex. PCIeSquirrel) connecté via Thunderbolt ou un emplacement M.2/PCIe.

### Prérequis
- Une connexion DMA réussie doit être active (vérifiée par `pcileech testmemread`).
- Un espace de stockage suffisant sur la machine de l'attaquant pour contenir le fichier mémoire résultant (ex. 16 Go de stockage pour 16 Go de RAM cible).

### Exécution logicielle
Utiliser **PCILeech** pour réaliser l'acquisition mémoire :
1.  **Lancer le dump :** Exécuter la commande suivante sur la machine de l'attaquant :
    `pcileech dump`
2.  **Surveiller le processus :** PCILeech commencera à lire la mémoire physique et à l'écrire dans un fichier.
3.  **Vérification :** * Le processus doit produire un fichier avec l'extension `.raw`.
    * Vérifier la taille du fichier pour s'assurer qu'elle correspond exactement à la quantité de RAM physique installée sur le système cible.
    * Exemple : Un système avec 32 Go de RAM doit produire un fichier `.raw` de 32 Go.

## Remédiation
- **Niveau Firmware/BIOS :** Activer **Intel VT-d** ou **AMD-Vi** (IOMMU) pour appliquer une isolation mémoire stricte et empêcher les périphériques non autorisés d'accéder à la carte mémoire physique complète.
- **Niveau système d'exploitation :** Activer la **protection DMA du noyau** pour s'assurer que le système d'exploitation conserve le contrôle des dispositifs capables de DMA et restreint leur accès à des régions mémoire spécifiques et autorisées.
- **Sécurité pré-démarrage :** Mettre en œuvre un mécanisme d'authentification pré-démarrage (PBA) pour s'assurer que le système ne démarre pas dans un environnement où le DMA peut être exploité avant l'authentification de l'utilisateur.
