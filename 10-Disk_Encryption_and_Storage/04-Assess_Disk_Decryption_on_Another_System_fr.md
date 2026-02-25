# Évaluer le déchiffrement du disque sur un autre système

|ID          |
|------------|
|CHSTG-DISK-04|

## Résumé

Ce contrôle évalue l'impact final d'une extraction de clé réussie en tentant de déchiffrer le disque cible sur un système non natif. Une fois les clés maîtresses de chiffrement (BitLocker, LUKS, etc.) obtenues via DMA, cold boot ou écoute du bus TPM, l'attaquant peut déplacer le disque vers une autre machine pour contourner toutes les mesures de sécurité du système d'exploitation natif. Monter un disque Windows chiffré BitLocker dans un environnement Linux en est un exemple classique, car cela permet à l'attaquant d'ignorer entièrement les listes de contrôle d'accès NTFS (ACL) une fois le volume déchiffré.

## Objectifs du test
- Vérifier que les clés de chiffrement ou le matériel récupéré lors des étapes d'audit précédentes sont valides et suffisants pour un accès complet aux données.
- Démontrer que le disque cible peut être déchiffré sur une autre plateforme ou un autre environnement matériel.
- Évaluer la capacité de contourner les permissions au niveau du système de fichiers (ACL) par montage multiplateforme.

## Comment tester
Ce test est réalisé après que le disque cible a été identifié comme chiffré et que les clés nécessaires ont été extraites.

### Prérequis
- Accès au disque cible (connecté via adaptateur USB ou port secondaire).
- Clés de chiffrement extraites (ex. FVEK pour BitLocker ou clé maîtresse pour LUKS).
- Un système secondaire exécutant un système d'exploitation alternatif (ex. une station de travail forensique Linux).

### Étapes d'exécution
1.  **Connexion du disque :** Connecter le disque cible au système Linux secondaire.
2.  **Identifier la partition :** Utiliser `lsblk` ou `blkid` pour identifier la partition chiffrée (ex. `/dev/sdb1`).
3.  **Tentative de déchiffrement :**
    - **Pour BitLocker :** Utiliser un outil tel que **dislocker** avec le matériel de clé extrait :
        `dislocker -V /dev/sdb1 -k <EXTRACTED_KEY_FILE> -- /mnt/tmp`
    - **Pour LUKS :** Utiliser **cryptsetup** :
        `cryptsetup open --type plain --key-file <EXTRACTED_KEY_FILE> /dev/sdb1 decrypted_volume`
4.  **Montage :** Monter le dispositif en boucle déchiffré sur un répertoire local :
    `mount -o loop /mnt/tmp/dislocker-file /mnt/target_data`
5.  **Vérification d'accès :** Parcourir les répertoires.
    * **Critère de succès (ÉCHEC) :** Le test est en échec si le disque se monte et que les fichiers (notamment les profils utilisateur protégés) sont accessibles et lisibles.

## Remédiation
Comme cette vulnérabilité résulte de clés de chiffrement compromises, il n'y a pas de remédiation directe pour le processus de déchiffrement une fois les clés perdues. La posture de sécurité doit se concentrer sur la prévention de l'extraction des clés en amont :
- **Prévenir la fuite des clés :** Renforcer les protections contre les attaques DMA, le cold boot et l'écoute du bus TPM comme détaillé dans les nœuds **CHSTG-DMA**, **CHSTG-MEM** et **CHSTG-TPM**.
