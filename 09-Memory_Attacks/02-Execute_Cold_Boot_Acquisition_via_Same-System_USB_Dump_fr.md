# Exécuter une acquisition cold boot via dump USB sur le même système

|ID          |
|------------|
|CHSTG-MEM-02|

## Résumé

Ce contrôle évalue la faisabilité de réaliser une attaque cold boot sans déplacer les modules RAM vers une autre machine. En refroidissant physiquement la RAM à des températures extrêmes, un attaquant peut forcer un redémarrage et démarrer le même système dans un environnement USB spécialisé pour vider le contenu de la mémoire. Cette technique est souvent utilisée lorsque la RAM est difficile à retirer ou lorsqu'un système secondaire compatible n'est pas disponible. Un obstacle critique dans cette attaque est la variable « Memory Overwrite Request » (MOR) du BIOS/UEFI, qui doit être contournée ou patchée pour empêcher le firmware d'effacer la RAM pendant la séquence de démarrage.

## Objectifs du test
- Démontrer que les données mémoire persistent après un redémarrage à chaud ou à froid lorsque la RAM est suffisamment refroidie.
- Contourner ou neutraliser avec succès la variable Memory Overwrite Request (MOR) au niveau BIOS.
- Acquérir un dump RAM complet à l'aide d'un outil UEFI sur USB sur le matériel cible d'origine.

## Comment tester
Ce test est effectué directement sur le système cible. Il nécessite la capacité de déclencher un redémarrage et d'accéder au menu de démarrage.

### Prérequis
- Accès à la RAM interne du système (via une trappe de maintenance ou en retirant le capot inférieur) sans démontage complet.
- Une clé USB contenant un outil de dump basé UEFI tel que **Memory-Dump-UEFI** ou **ram-dump-efi**.

### Étapes d'exécution
1.  **Refroidissement :** Pendant que le système est en fonctionnement ou en état de veille, utiliser un spray d'air comprimé tenu à l'envers pour pulvériser directement les modules RAM, abaissant la température à environ **-60 °C**.
2.  **Redémarrage forcé :** Effectuer un cycle d'alimentation brutal de la machine (ex. maintenir le bouton d'alimentation ou débrancher et rebrancher rapidement la batterie/alimentation).
3.  **Patch du bit MOR :** Si le BIOS tente d'effacer la mémoire, utiliser un outil ou script spécialisé pour patcher la variable NVRAM **Memory Overwrite Request (MOR)** à `0`. Cela indique au BIOS qu'aucun effacement n'est requis au prochain démarrage.
4.  **Démarrage sur USB :** Déclencher immédiatement le menu de démarrage et sélectionner la clé USB contenant l'environnement de dump UEFI.
5.  **Acquisition :**
    - Lancer l'utilitaire de dump depuis le shell UEFI (ex. `Memory-Dump-UEFI`).
    - Copier la plage de mémoire physique sur le stockage USB.
    - **Critère de succès :** Un dump mémoire exploitable est obtenu contenant des vestiges de la session du système d'exploitation précédente (ex. chaînes en clair, en-têtes de processus).

## Remédiation
- **Chiffrement mémoire :** Activer le chiffrement RAM matériel tel que **Intel Total Memory Encryption (TME)** ou **AMD Transparent SME (TSME)** pour garantir que les données restent chiffrées même si les charges physiques sont préservées.
- **Brouillage mémoire :** Activer le brouillage mémoire au niveau BIOS pour obscurcir les motifs de données dans les cellules DRAM.
