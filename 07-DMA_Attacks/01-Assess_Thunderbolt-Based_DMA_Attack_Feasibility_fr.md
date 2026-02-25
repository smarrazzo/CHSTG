# Évaluer la faisabilité d'attaque DMA via Thunderbolt

|ID          |
|------------|
|CHSTG-DMA-01|

## Résumé

Les interfaces Thunderbolt offrent un accès externe au bus PCIe haute vitesse. Ce contrôle évalue la faisabilité de réaliser des attaques d'accès direct à la mémoire (DMA) via ces ports. En exploitant le caractère plug-and-play de Thunderbolt, un attaquant peut connecter un périphérique malveillant pour lire ou écrire la mémoire système sans démonter le matériel. Ceci est particulièrement critique lorsqu'un appareil est laissé sans surveillance en état de veille (S3 ou Modern Standby), car cela peut permettre l'extraction de clés de chiffrement ou l'injection de code malveillant dans le noyau.

## Objectifs du test
- Vérifier si les ports Thunderbolt du système permettent un accès DMA non autorisé.
- Évaluer la capacité de lire la RAM système pour extraire des données sensibles (ex. identifiants, clés de chiffrement).
- Évaluer la capacité d'écrire dans la RAM système pour manipuler le noyau du système d'exploitation ou élever les privilèges.

## Comment tester
Ce test doit être effectué sur un système en fonctionnement sans accès physique interne, en se concentrant sur les ports externes.

### Prérequis
- S'assurer que les protections anti-DMA identifiées dans la section **Sécurité du micrologiciel** (ex. IOMMU, VT-d) sont soit désactivées soit en cours d'évaluation de contournement.

### Configuration matérielle
Selon la version Thunderbolt disponible sur la cible (Thunderbolt 2, 3 ou 4), utiliser la chaîne d'adaptateurs appropriée pour connecter une carte FPGA malveillante :
1.  **Carte DMA FPGA :** Utiliser un dispositif tel que **PCIeSquirrel**.
2.  **Pour Thunderbolt 3/4 :** Utiliser un **adaptateur/dock e-GPU** pour relier la carte PCIe au port USB-C/Thunderbolt.
3.  **Pour Thunderbolt 2 (legacy) :** Utiliser une chaîne d'adaptateurs : **PCIe vers ExpressCard** -> **ExpressCard vers Thunderbolt 2 (Mini DisplayPort)**.
4.  **Intergénération :** Si nécessaire, utiliser un **adaptateur Thunderbolt 2 vers Thunderbolt 3**.

### Exécution logicielle
Utiliser **PCILeech** pour vérifier l'accès mémoire :
- **Vérifier l'accès en lecture :** Exécuter la commande suivante pour vérifier si la RAM peut être lue (nécessaire pour le dump mémoire) :
    `pcileech testmemread`
- **Vérifier l'accès en écriture :** Exécuter la commande suivante pour vérifier l'accès en écriture aléatoire à la RAM (nécessaire pour l'injection de code) :
    `pcileech testmemrandwrite`

## Remédiation
- **Niveau Firmware/BIOS :** Activer **VT-d** (Intel Virtualization Technology for Directed I/O) ou **AMD-Vi**. Configurer les niveaux de sécurité Thunderbolt sur **Autorisation utilisateur (SL1)** ou **Connexion sécurisée (SL2)** pour empêcher la connexion de périphériques DMA non autorisés.
- **Niveau système d'exploitation :** Activer la **protection DMA du noyau** (sous Windows) ou s'assurer que l'IOMMU est strictement appliqué (sous Linux) pour isoler les espaces mémoire des périphériques externes.
- **Sécurité pré-démarrage :** Désactiver les « Option ROMs » Thunderbolt/PCIe et l'accès DMA pré-démarrage dans les paramètres du BIOS.
