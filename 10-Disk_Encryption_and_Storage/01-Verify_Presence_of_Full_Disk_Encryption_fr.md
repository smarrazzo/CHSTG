# Vérifier la présence du chiffrement complet du disque

|ID          |
|------------|
|CHSTG-DISK-01|

## Résumé

La première ligne de défense pour les données au repos est le chiffrement complet du disque (FDE). Ce contrôle vise à vérifier si le support de stockage principal (SSD/HDD) est protégé par des technologies telles que BitLocker, LUKS, FileVault. Identifier la présence du chiffrement est un prérequis pour les tests ultérieurs impliquant l'extraction de clés ou la manipulation de données hors ligne.

## Objectifs du test
- Confirmer si le volume disque est chiffré ou si les données sont stockées en clair.
- Identifier la technologie de chiffrement spécifique et la version utilisée.
- Déterminer si les données sont accessibles lorsque le disque est retiré de son environnement natif.

## Comment tester
Ce test se concentre sur la vérification du statut de chiffrement en tentant d'accéder aux données depuis un système externe.

### Prérequis
- Accès au support de stockage (ex. via une trappe de maintenance ou baie de disque externe) sans effectuer un démontage complet du système.

### Étapes d'exécution
1.  **Retrait/Connexion du disque :** Connecter le disque cible à une station de travail forensique secondaire ou à un autre ordinateur à l'aide d'un adaptateur USB vers NVMe/SATA.
    * **AVERTISSEMENT CRITIQUE :** Ne **pas** tenter de démarrer un système d'exploitation Live (USB) sur le matériel cible lui-même pour effectuer cette vérification. Cela peut modifier les **Registres de configuration de plateforme (PCR) du TPM**, ce qui peut invalider la vérification d'intégrité et empêcher le système d'exploitation d'origine de démarrer ultérieurement, bloquant ainsi les tests d'audit.
2.  **Tentative de montage :** Sur le système secondaire, utiliser les outils de gestion des disques pour inspecter la partition.
    * **Windows :** Utiliser `diskmgmt.msc` ou `manage-bde -status`.
    * **Linux :** Utiliser `lsblk` et `blkid` pour vérifier la présence de `crypto_LUKS` ou de types de système de fichiers inconnus.
3.  **Validation :**
    - Si le système demande un mot de passe/clé de récupération et identifie un en-tête de chiffrement connu, le disque est chiffré.
    - Si les partitions se montent automatiquement et que les fichiers sont lisibles, le disque **n'est pas** chiffré.

## Remédiation
- **Activer le chiffrement :** Activer le chiffrement complet du disque (ex. BitLocker sous Windows, LUKS sous Linux) pour toutes les partitions système et données.
- **Authentification pré-démarrage :** S'assurer que le chiffrement exige un secret fort (PIN, phrase de passe ou clé matérielle) avant le début du processus de démarrage du système d'exploitation.
