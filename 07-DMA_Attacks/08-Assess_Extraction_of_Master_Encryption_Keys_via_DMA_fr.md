# Évaluer l'extraction des clés maîtresses de chiffrement via DMA

|ID          |
|------------|
|CHSTG-DMA-08|

## Résumé

L'objectif ultime de nombreuses attaques DMA est l'extraction des clés maîtresses du chiffrement complet du disque (FDE). Une fois qu'un attaquant a réussi à élever les privilèges au niveau root ou SYSTEM par injection DMA (comme vu dans CHSTG-DMA-07), il peut utiliser les outils natifs du système d'exploitation pour révéler les protecteurs de chiffrement ou les clés maîtresses stockées en mémoire volatile. Cela permet à l'attaquant de déchiffrer le disque hors ligne ou de maintenir un accès persistant aux données même si le système est ensuite arrêté.

## Objectifs du test
- Utiliser l'accès privilégié obtenu via le DMA pour récupérer les clés maîtresses de chiffrement disque ou les protecteurs de récupération.
- Valider la capacité d'effectuer le déchiffrement hors ligne du support de stockage cible à l'aide du matériel extrait.
- Démontrer le contournement de la sécurité BitLocker (Windows) ou LUKS/dm-crypt (Linux) par manipulation mémoire.

## Comment tester
Ce test constitue la phase finale d'une chaîne d'exploitation DMA. Il est effectué sur le système cible en fonctionnement à l'aide d'un shell privilégié. Aucun démontage n'est requis.

### Prérequis
- Une élévation de privilèges réussie vers **NT AUTHORITY\SYSTEM** (Windows) ou **root** (Linux) doit avoir été obtenue par injection DMA (voir **CHSTG-DMA-07**).
- Le système cible doit avoir le chiffrement complet du disque activé (ex. BitLocker ou LUKS).

### Exécution logicielle
Depuis le shell privilégié obtenu via **PCILeech**, exécuter les commandes suivantes pour extraire les clés :

1.  **Pour Windows (BitLocker) :**
    Utiliser l'outil de gestion BitLocker natif pour afficher les protecteurs de clé :
    `manage-bde -protectors -get c:`
    - **Critère de succès :** La commande renvoie le mot de passe numérique (clé de récupération) ou le matériel de clé externe.

2.  **Pour Linux (LUKS/dm-crypt) :**
    Utiliser l'outil de configuration device mapper pour extraire les clés de chiffrement actives du noyau :
    `dmsetup table --showkeys`
    - **Critère de succès :** La commande affiche la clé hex maîtresse utilisée pour le mappage du volume chiffré.

## Remédiation
- **Niveau Firmware/BIOS :** Activer **Intel VT-d** ou **AMD-Vi** (IOMMU) pour appliquer l'isolation mémoire au niveau matériel, empêchant les périphériques non autorisés d'interagir avec la RAM système où les clés sont stockées.
- **Niveau système d'exploitation :** Activer la **protection DMA du noyau** pour restreindre l'accès DMA des dispositifs non de confiance.
- **Politique de chiffrement :** Mettre en œuvre BitLocker avec un **PIN renforcé** ou une clé de démarrage (USB) plutôt que de s'appuyer uniquement sur le TPM (mode « TPM uniquement »), car le PIN/clé est requis pour libérer la clé maîtresse en mémoire pendant le processus de démarrage.
- **Protections pré-démarrage :** Utiliser l'authentification pré-démarrage (PBA) pour s'assurer que le disque reste chiffré et que les clés ne sont pas chargées en mémoire tant qu'un utilisateur n'est pas physiquement présent et authentifié.
