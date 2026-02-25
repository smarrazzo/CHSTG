# Évaluer l'extraction des clés maîtresses de chiffrement depuis un dump mémoire

|ID          |
|------------|
|CHSTG-MEM-04|

## Résumé

Une fois un dump mémoire acquis (via DMA, cold boot ou autres méthodes), l'accent se déplace vers l'analyse forensique pour localiser et extraire les secrets cryptographiques. La mémoire volatile est une cible de choix car elle stocke fréquemment les clés de chiffrement complet du disque (FDE), telles que la clé de chiffrement de volume complète BitLocker (FVEK) ou les clés maîtresses LUKS, en clair pour permettre au processeur d'effectuer le chiffrement et le déchiffrement en temps réel du trafic disque. Ce contrôle évalue la capacité d'un attaquant à utiliser des outils forensiques pour récupérer ces clés et déchiffrer ensuite le stockage du système hors ligne.

## Objectifs du test
* Analyser le dump de mémoire physique pour identifier les structures associées à BitLocker, LUKS ou d'autres fournisseurs de chiffrement.
* Extraire les clés maîtresses de chiffrement ou les planifications de clés de l'image RAM à l'aide de frameworks forensiques.
* Valider l'utilité du matériel extrait en tentant de déchiffrer le volume disque cible.

## Comment tester
Ce test est effectué sur une station de travail forensique à l'aide d'une image mémoire acquise lors des étapes précédentes. Aucun accès direct au matériel cible n'est requis pendant la phase d'analyse.

### Prérequis
- Un dump RAM physique complet (ex. `.raw`, `.bin` ou `.dmp`) obtenu via des contrôles tels que **CHSTG-MEM-01** ou **CHSTG-DMA-05**.
- Outils forensiques installés, tels que **Volatility 3**, **Rekall** ou des scripts spécialisés comme `find-aes`.

### Étapes d'exécution
1.  **Analyser les métadonnées du dump :** Utiliser **Volatility 3** pour identifier le système d'exploitation et la version du noyau associés au dump afin d'utiliser les symboles corrects.
2.  **Rechercher les clés de chiffrement :**
    * **Balayage automatisé :** Exécuter des plugins conçus pour trouver les planifications de clés AES ou les métadonnées de chiffrement spécifiques :
        - Pour Windows/BitLocker : Utiliser des outils ou plugins qui recherchent les en-têtes « FVE » (Full Volume Encryption) ou les planifications AES-256.
        - Pour Linux/LUKS : Rechercher dans l'espace mémoire noyau le matériel de clé maîtresse utilisé par `dm-crypt`.
3.  **Recherche forensique manuelle :** Si les outils automatisés échouent, utiliser `strings` ou des éditeurs hexadécimaux pour rechercher des motifs liés aux clés ou des structures connues dans les régions mémoire associées aux pilotes disque.

## Remédiation
- **Chiffrement au niveau matériel :** Activer **Intel Total Memory Encryption (TME)** ou **AMD Transparent SME (TSME)** pour chiffrer l'intégralité de la mémoire système au niveau matériel, rendant les données dumpées illisibles sans la clé liée au matériel.
- **Brouillage mémoire :** S'assurer que le BIOS/UEFI a le brouillage mémoire activé pour perturber les motifs physiques des clés en DRAM.
- **Protection des clés :** Configurer le système d'exploitation pour utiliser des protecteurs « TPM + PIN ». Cela garantit que la clé maîtresse n'est chargée en mémoire qu'après que l'utilisateur a fourni un secret, réduisant la fenêtre d'opportunité pour l'extraction par cold boot ou DMA.
