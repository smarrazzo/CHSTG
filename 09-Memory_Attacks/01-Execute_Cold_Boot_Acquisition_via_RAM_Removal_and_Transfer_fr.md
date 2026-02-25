# Exécuter une acquisition cold boot via retrait et transfert de la RAM

|ID          |
|------------|
|CHSTG-MEM-01|

## Résumé

L'attaque « Cold Boot » exploite la propriété physique de la DRAM, où les données ne disparaissent pas instantanément lorsque l'alimentation est coupée. À température ambiante, la rémanence des données ne dure que quelques secondes, mais en congelant les puces mémoire, la période de rétention peut être prolongée de plusieurs minutes. Ce contrôle évalue le risque qu'un attaquant retire physiquement les modules RAM d'un système en fonctionnement ou récemment arrêté pour en vider le contenu sur une machine secondaire, contournant ainsi les protections mémoire au niveau du système d'exploitation et acquérant des données sensibles comme les clés de chiffrement ou les identifiants.

## Objectifs du test
- Démontrer la rémanence des données en DRAM en abaissant la température de fonctionnement.
- Transférer avec succès les modules RAM « congelés » vers un système récepteur sans perte de données.
- Réaliser une acquisition mémoire complète en utilisant un environnement pré-OS minimal sur la machine réceptrice.

## Comment tester
Ce test implique une manipulation physique des modules RAM et nécessite une machine « réceptrice » secondaire avec des emplacements mémoire compatibles.

### Prérequis
- Un système cible avec des modules RAM amovibles (SO-DIMM ou DIMM).
- Un système récepteur avec les mêmes caractéristiques RAM (ex. DDR4, DDR5).
- Une clé USB contenant un outil de dump basé UEFI tel que **Memory-Dump-UEFI** ou **ram-dump-efi**.

### Étapes d'exécution
1.  **Préparation :** Avoir le système récepteur ouvert et prêt à recevoir les modules RAM.
2.  **Congélation :** Avec le système cible en fonctionnement (ou en état de veille), utiliser un spray d'air comprimé tenu à l'envers pour pulvériser les puces RAM. Cela peut abaisser la température à environ **-60 °C**.
3.  **Coupure d'alimentation :** Couper brutalement l'alimentation du système cible en retirant la batterie et en débranchant l'alimentation pour empêcher le BIOS d'effectuer un effacement mémoire.
4.  **Transfert :** Retirer rapidement les modules RAM du système cible et les installer dans le système récepteur.
5.  **Acquisition :**
    - Mettre le système récepteur sous tension et démarrer immédiatement dans le shell UEFI USB.
    - Exécuter l'outil de dump (ex. `Memory-Dump-UEFI`) pour copier le contenu de la RAM transférée sur la clé USB.
    - **Critère de succès :** Une image `.bin` ou `.raw` de la mémoire est obtenue et contient des chaînes ou structures lisibles de la session du système cible.

## Remédiation
- **Chiffrement mémoire :** Activer les fonctionnalités de chiffrement mémoire matériel telles que **Intel Total Memory Encryption (TME)** ou **AMD Transparent SME (TSME)**. Cela garantit que même si les données sont récupérées depuis les puces, elles restent chiffrées et illisibles.
- **Brouillage mémoire :** S'assurer que le brouillage mémoire est activé dans le BIOS pour empêcher la reconstruction facile de motifs simples.
- **Bit TCG MOR :** Mettre en œuvre le support du bit **Memory Overwrite Request (MOR)**, qui indique au BIOS d'écraser la mémoire au démarrage si le système d'exploitation ne s'est pas arrêté proprement.
