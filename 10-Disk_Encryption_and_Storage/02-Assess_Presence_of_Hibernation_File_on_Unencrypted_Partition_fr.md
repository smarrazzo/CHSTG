# Évaluer la présence du fichier d'hibernation sur une partition non chiffrée

|ID          |
|------------|
|CHSTG-DISK-02|

## Résumé

L'hibernation est un état d'économie d'énergie où le système d'exploitation enregistre le contenu actuel de la RAM dans un fichier sur le disque dur (ex. `hiberfil.sys` sous Windows) avant de couper l'alimentation. Comme la RAM contient du matériel sensible—notamment les clés maîtresses de chiffrement pour les volumes secondaires, les identifiants utilisateur et les jetons de session actifs—le fichier d'hibernation devient une image statique des secrets du système. Si ce fichier est stocké sur une partition non chiffrée ou si le chiffrement disque est contourné, un attaquant peut extraire ces clés pour compromettre le reste du système.

## Objectifs du test
- Localiser et identifier le fichier d'hibernation ou la partition swap sur le support de stockage cible.
- Déterminer si les données d'hibernation sont stockées sur une partition qui ne dispose pas du chiffrement complet du disque (FDE).
- Vérifier l'accessibilité des artefacts mémoire du fichier d'hibernation sans exiger le secret principal de l'utilisateur.

## Comment tester
Ce test implique l'inspection de la configuration de stockage de l'appareil cible depuis une station de travail forensique externe.

### Prérequis
- Le système cible doit avoir été placé en état d'hibernation (S4) avant le test.
- Le disque cible doit être connecté à un système secondaire pour analyse hors ligne (voir les avertissements dans **CHSTG-DISK-01** concernant l'invalidation des PCR).

### Étapes d'exécution
1.  **Analyse des partitions :** Utiliser un utilitaire disque (ex. Gestion des disques, GParted ou fdisk) pour lister toutes les partitions sur le disque cible.
2.  **Localiser les données d'hibernation :**
    * **Windows :** Rechercher le fichier `hiberfil.sys` à la racine de la partition système (ou de toute partition visible).
    * **Linux :** Identifier la partition `swap` ou les fichiers swap pouvant être utilisés pour les opérations de mise en veille sur disque.
3.  **Vérification d'accès :** Tenter de copier le fichier ou de vider la partition swap.
    * **Critère de succès (ÉCHEC) :** Le test est en échec si le fichier d'hibernation est trouvé sur une partition qui ne requiert pas de mot de passe de déchiffrement pour être lue.
    * **Analyse :** Même si la partition système est chiffrée, vérifier si une partition « Données » secondaire est non chiffrée et contient un fichier d'hibernation déplacé.

## Remédiation
- **Désactiver l'hibernation :** La défense la plus efficace est de désactiver complètement la fonctionnalité d'hibernation pour empêcher l'écriture d'images mémoire sur le disque.
    - *Commande Windows :* `powercfg -h off`
- **Appliquer le chiffrement complet du disque :** S'assurer que l'intégralité du disque, y compris toutes les zones swap et partitions secondaires, est protégée par un chiffrement fort (ex. BitLocker ou LUKS).
- **Mise en veille RAM uniquement :** Configurer le système pour n'utiliser que la veille (S3) ou Modern Standby, à condition que les protections mémoire appropriées (TME/SME) soient actives pour atténuer les risques de cold boot.
