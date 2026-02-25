# Évaluer l'extraction des clés maîtresses depuis le fichier d'hibernation

|ID          |
|------------|
|CHSTG-DISK-03|

## Résumé

Le fichier d'hibernation est un instantané compressé de la mémoire volatile du système (RAM) enregistré sur le stockage persistant. Comme les clés de chiffrement disque doivent résider en RAM pour que le système d'exploitation effectue le traitement des données en temps réel, ces clés sont inévitablement écrites dans le fichier d'hibernation (`hiberfil.sys` sous Windows ou la partition `swap` sous Linux) lorsque le système entre en état S4. Ce contrôle se concentre sur l'analyse forensique de ce fichier pour extraire le matériel cryptographique, permettant à un attaquant de déchiffrer les partitions hors ligne.

## Objectifs du test
- Réaliser une analyse hors ligne des données d'hibernation ou swap pour identifier les métadonnées de chiffrement.
- Rechercher et extraire les clés maîtresses telles que la clé maîtresse de volume (VMK), la clé de chiffrement de volume complète (FVEK) ou les clés maîtresses LUKS.
- Valider les clés extraites en déchiffrant et montant avec succès les volumes chiffrés associés.

## Comment tester
Ce test est réalisé sur une station de travail forensique à l'aide du fichier d'hibernation ou du dump swap acquis lors des étapes d'analyse disque précédentes (voir **CHSTG-DISK-02**).

### Prérequis
- Une copie du fichier d'hibernation du système cible (ex. `hiberfil.sys`) ou un dump brut de la partition swap.
- Outils forensiques capables de traiter les fichiers d'hibernation, tels que **Volatility 3**, **Hibernation Recon** ou des scripts de décompression spécialisés.

### Étapes d'exécution
1.  **Décompression :** Les fichiers d'hibernation sont généralement compressés ou encapsulés par le système d'exploitation. Utiliser un outil pour convertir le fichier au format d'image mémoire « raw » standard.
2.  **Balayage des clés :**
    - **Balayage automatisé :** Exécuter des plugins spécialisés (ex. `windows.bitlocker` dans Volatility) pour rechercher dans l'image mémoire les structures BitLocker FVEK ou VMK.
    - **Analyse manuelle :** Rechercher les planifications de clés AES ou les en-têtes de clé maîtresse LUKS dans l'espace d'adressage associé aux tampons des pilotes disque.

## Remédiation
- **Désactiver l'hibernation :** La remédiation la plus efficace est de désactiver complètement la fonctionnalité d'hibernation pour garantir qu'aucun instantané RAM ne soit jamais écrit sur le disque.
    - **Windows :** Exécuter `powercfg -h off` depuis une invite d'administration.
    - **Linux :** Désactiver les cibles hibernate/suspend-to-disk dans `systemd` ou supprimer les exigences de partition/fichier swap.
- **Chiffrer les données d'hibernation :** Si l'hibernation est requise, s'assurer qu'elle est enregistrée strictement dans une partition protégée par le chiffrement complet du disque (FDE) avec authentification pré-démarrage.
