# Introduction et objectifs

## Introduction

Le but de cette méthodologie de test est d’évaluer la robustesse et la configuration bas niveau d’un poste utilisateur.
Elle s’applique dans un contexte où le commanditaire de l’audit de sécurité n’est pas le fabricant du poste, mais une entreprise ayant acquis un parc de machines auprès d’un constructeur (HP, Dell, etc.), et souhaitant évaluer les risques inhérents à leur conception.

Certaines remédiations proposées peuvent être particulièrement contraignantes (par exemple l’application d’un mot de passe ATA). Cependant, elles servent de référence pour viser le niveau de sécurité maximal ; il appartient au commanditaire de juger leur mise en œuvre et d’évaluer les risques associés.

## Phases de l’audit

La méthodologie suit le processus suivant :

![Schéma du processus d’audit](../Process_hard_Full.png)

Ce processus est susceptible d’évoluer en fonction des différentes mises à jour de la méthodologie.
**À noter :** sur l’image, toutes les cases en rouge signalent un risque de destruction, de perte de données ou de matériel.

La démarche inclut les phases suivantes :

- **Phase de reconnaissance :**
  - Sans accès physique
  - Avec accès physique

- **Attaques liées au firmware :**
  - Suppression des mots de passe d’accès
  - Suppression des protections

- **Attaques de type DMA :**
  - Via les ports PCIe
  - Via Thunderbolt

- **Attaques par interception de signaux**

- **Attaques de type cold boot**

Enfin, la phase de post-exploitation permettra de prendre le contrôle du système d’exploitation.

L’objectif est d’identifier, à chaque étape, les vulnérabilités intrinsèques à la conception du poste et, chaque fois que possible, de proposer des remédiations appropriées.

## Outils et techniques

Chaque phase de l’audit utilise des techniques spécifiques, des outils matériels et logiciels. Voici une présentation générale des techniques et outils utilisables.

### Soudure

Dans de nombreux cas, il est nécessaire de dessouder des composants électroniques pour mener à bien certaines attaques.
De plus, dans certains cas, il est utile de souder des sondes sur des composants pour en intercepter les signaux.

Pour cela, il est important d’avoir des outils adaptés, tels que :

- Station de soudure à température contrôlée
- Station d’air chaud à température contrôlée
- Microscope trinoculaire équipé d’une bague lumineuse, utilisé pour l’observation des composants et la réalisation de soudures fines
- Pinces de précision (≈ 100 µm)
- Fils de précision (≈ 10 µm), ruban Kapton, ruban aluminium, etc.
- Stencils de différents formats pour opérations de reballing si nécessaire
- Plusieurs types d’étain et de pâtes à braser, adaptés à différentes plages de température

![Équipement de soudure](img/Soudure.png)

### Analyse et mesure

Un environnement pour l’analyse des signaux électroniques est également utile. Il doit comporter au moins les outils suivants :

- Oscilloscope 4 voies, 250 MHz, avec sondes adaptées
- Alimentation de laboratoire à tension et courant contrôlés
- Sondes de mesure de différents types (ex. : PCBite)
- Pinces et accessoires variés pour les manipulations et connexions temporaires

### Modification de firmware

#### Techniques utilisées

La modification du firmware de la carte mère du poste audité intervient lorsqu’un mot de passe d’accès au BIOS/UEFI est présent.
En effet, la réalisation de certaines attaques matérielles (telles que les attaques DMA ou cold boot) nécessite un accès aux paramètres du BIOS/UEFI, notamment afin de désactiver des mécanismes de protection.
Avant toute modification, les auditeurs procèdent systématiquement à un dump complet du firmware, afin de constituer un état initial de référence permettant un retour arrière en cas de problème.
La modification du firmware étant une opération de très bas niveau, elle comporte un risque de dysfonctionnement, voire de rendre le poste inutilisable.
Pour effectuer ces modifications, les auditeurs disposent de plusieurs approches possibles :

- Réutilisation d’un firmware tiers trouvé sur Internet
- Utilisation de programmes de suppression de mot de passe BIOS
- Modification manuelle des variables NVRAM
- Injection de code malveillant au niveau du firmware (modules DXE)

Chacune de ces méthodes présente un risque de panne ou d’instabilité du poste audité et doit être mise en œuvre avec précaution dans un cadre maîtrisé.

#### Outils

Pour la modification du firmware, les auditeurs disposent de plusieurs équipements matériels et logiciels adaptés aux opérations de lecture, d’analyse et de reprogrammation de mémoires non volatiles.

##### Équipements matériels

- **Programmateur XGecu Pro T56** (~400 €)  
  Programmateur professionnel de haute qualité permettant la lecture et l’écriture rapides d’un large éventail de composants mémoire (Flash, EEPROM, etc.), y compris des puces jusqu’à 48 broches. Il offre une excellente compatibilité et une grande fiabilité pour les opérations sensibles sur le firmware.

- **Programmateur CH341A** (~15 €)  
  Programmateur économique et largement répandu, permettant la reprogrammation de puces Flash NOR (25QXXX) et EEPROM (24C/24QXXX) jusqu’à 8 broches. Bien que plus limité et plus lent que le T56, cet équipement est suffisant pour la majorité des opérations de reprogrammation de firmware d’ordinateurs portables.

- **Pince SOIC-8** (~5 €)  
  Accessoire permettant la lecture et l’écriture in situ de puces au format SOIC-8, sans dessoudage, réduisant ainsi les risques de détérioration de la carte mère.

- **Adaptateur TSOP-8**  
  Utilisé lorsque le dessoudage du composant est nécessaire. Cet adaptateur permet de connecter facilement une puce TSOP-8 au programmateur pour sa reprogrammation.

![Programmateur XGecu Pro T56 et pince SOIC-8](img/Xgecu.png)
Programmateur XGecu Pro T56 avec une pince SOIC-8 pour la lecture ou l’écriture in situ de puces mémoire.

![Programmateur CH341A et adaptateur QFN8 ➔ DIP8](img/CH341_adapter.png)
Programmateur CH341A connecté à un adaptateur QFN8 vers DIP8, permettant la manipulation de différents formats de puces mémoire.


##### Outils logiciels

- **XGPro** — Logiciel officiel associé au programmateur XGecu Pro T56, permettant la gestion des opérations de lecture, d’écriture, de vérification et d’identification des composants mémoire.

- **UEFITool** — Outil open source destiné à l’analyse des firmwares UEFI. Il permet d’explorer la structure interne du firmware (volumes, fichiers, modules DXE/PEI), d’identifier des composants critiques et de préparer des modifications ciblées.

- **MEAnalyze** — Outil spécialisé permettant l’analyse des firmwares Intel Management Engine (ME). Il fournit des informations détaillées sur la version, l’état de configuration, les fonctionnalités activées ainsi que d’éventuelles incohérences ou faiblesses de configuration.

- **IDA (Interactive Disassembler)** — Outil de reverse engineering utilisé pour analyser le code binaire présent dans le firmware, notamment les modules DXE ou les routines spécifiques liées à la sécurité. Il permet une compréhension approfondie du fonctionnement interne du firmware et la réalisation de modifications avancées.

### Interception de signaux

#### Techniques utilisées

L’attaque par interception physique du TPM consiste à intercepter les communications matérielles entre le TPM (Trusted Platform Module) et le processeur (CPU).
Lorsqu’un système de chiffrement du disque est utilisé au niveau du système d’exploitation et qu’aucun code PIN n’est configuré, la clé de déchiffrement est transmise automatiquement par le TPM au CPU lors du démarrage.
Cette clé transite en clair sur le bus de communication matériel reliant le TPM au CPU, généralement de type SPI ou I²C.
En disposant d’un accès physique à la carte mère, un attaquant peut placer des sondes matérielles sur les points de communication de ce bus.
Ces sondes sont reliées à un analyseur logique, permettant de capturer et décoder les échanges, et ainsi d’identifier et récupérer la clé de déchiffrement échangée.
Une fois cette clé obtenue, le contenu du disque chiffré peut être déchiffré hors ligne, sans nécessiter l’authentification de l’utilisateur ni l’accès au système d’exploitation.

#### Présentation des outils

Pour la réalisation d’attaques par interception des communications du TPM, les auditeurs disposent des équipements matériels et logiciels suivants.

##### Équipements matériels

- **Sondes PCBite SP10** (~250 €)  
  Sondes de type pogo permettant un contact temporaire et précis sur des points de test, des pistes ou des composants CMS sans nécessiter de soudure. Ces sondes sont particulièrement adaptées à l’interception de signaux sur des bus de communication (SPI, I²C) situés à proximité du TPM ou des composants associés.

- **DSLogic U3Pro32** (~400 €)  
  Analyseur logique 32 canaux capable de fonctionner jusqu’à 1 GHz d’échantillonnage. Cet équipement permet la capture fiable de signaux haute fréquence, indispensable pour l’analyse des communications TPM lors des phases critiques du démarrage du système.

![U3Pro32 et sondes PCBite](img/U3Pro32_pcbite.png)
Analyseur logique U3Pro32 connecté à des sondes PCBite SP10.

##### Outils logiciels

- **DSView** — Logiciel associé à l’analyseur logique DSLogic, permettant la visualisation, l’enregistrement et l’analyse des signaux capturés. DSView intègre des modules de décodage de protocoles, notamment pour les bus SPI, facilitant l’interprétation des échanges entre le TPM et le CPU et l’identification d’informations sensibles échangées.

### Attaque DMA

#### Techniques utilisées

L’attaque DMA ne constitue pas, à proprement parler, l’exploitation d’une vulnérabilité logicielle. Elle repose sur le détournement d’une fonctionnalité matérielle légitime.
Le DMA (Direct Memory Access) est un mécanisme matériel permettant à un périphérique PCIe d’interagir directement avec la mémoire vive (RAM) sans passer par le processeur (CPU), afin d’améliorer les performances. Cette fonctionnalité est essentielle au fonctionnement de périphériques à haut débit, tels que les cartes graphiques ou certains contrôleurs réseau.
Le principe du DMA n’est pas spécifique aux ordinateurs : il est largement utilisé dans de nombreux équipements électroniques.
Afin de pallier l’accès direct et non contrôlé à la mémoire RAM tout en conservant de bonnes performances, la fonctionnalité IOMMU (Input-Output Memory Management Unit) a été introduite. Elle permet une virtualisation de l’espace mémoire, en attribuant à chaque périphérique un espace mémoire dédié, l’empêchant ainsi d’accéder à la mémoire critique du noyau du système d’exploitation.
Cependant, ces protections IOMMU peuvent être désactivées dans le BIOS/UEFI de certaines cartes mères. Une fois désactivées, les périphériques PCIe retrouvent un accès complet à la mémoire RAM.
L’attaque DMA consiste alors à utiliser un périphérique PCIe malveillant, connecté à la fois au bus PCIe du poste cible et à un système contrôlé par l’attaquant.
Ce périphérique permet à l’attaquant de lire et d’écrire directement dans la mémoire RAM de la machine victime.
Du fait de cet accès étendu à l’intégralité de la mémoire vive, l’attaquant dispose de privilèges équivalents, voire supérieurs, à ceux du système d’exploitation, rendant possibles des compromissions majeures du poste.

#### Présentation des outils

Pour la réalisation d’attaques de type DMA (Direct Memory Access), les auditeurs disposent des équipements matériels et logiciels suivants.

##### Équipements matériels

- **PCI Squirrel** (~250 €)  
  Carte malveillante au format PCIe x1, conçue pour permettre un accès direct à la mémoire vive (RAM) de la machine cible via le bus PCIe. Cette carte agit comme un pont entre le poste audité et le système de l’attaquant, autorisant la lecture et l’écriture en mémoire lorsque les protections IOMMU / VT-d sont désactivées ou mal configurées.

- **Adaptateurs PCIe** (divers formats, ~1 € à quelques euros)  
  Ensemble d’adaptateurs permettant de convertir les différents formats physiques du bus PCIe afin d’exploiter les ports disponibles sur les ordinateurs portables et stations de travail. Bien que les formats diffèrent, ces interfaces reposent toutes sur le même bus PCIe. Exemples d’adaptateurs utilisés :
  - PCIe x4 → NVMe (M-Key)
  - PCIe B-Key → M+B Key
  - NVMe → M+B Key
  - NVMe → A+E Key
  - NVMe → PCIe x1

![PcieSquirrel et adaptateurs PCIe](img/PCIESquirrel_adapter.png)
Exemple de la carte PcieSquirrel accompagnée de divers adaptateurs PCIe permettant l’interfaçage avec différents ports présents sur les postes audité. L’utilisation appropriée de ces adaptateurs maximise la compatibilité avec les configurations matérielles rencontrées lors des audits.


  En complément, les auditeurs disposent également des adaptateurs suivants, permettant l’exploitation du bus PCIe via Thunderbolt :
  - Adaptateur PCIe → ExpressCard : permet l’export du bus PCIe vers un format ExpressCard, historiquement utilisé sur certains ordinateurs portables professionnels.
  - Adaptateur ExpressCard → Thunderbolt 2 : permet de transporter le bus PCIe au travers d’une interface Thunderbolt 2.
  - Adaptateur Thunderbolt 2 → Thunderbolt 3 : assure la compatibilité avec les ports Thunderbolt 3 (USB-C) présents sur les équipements récents.

  L’enchaînement de ces adaptateurs permet de transporter le bus PCIe via une interface Thunderbolt, rendant possibles des attaques DMA à chaud (plug-and-play) sur des systèmes exposant un port Thunderbolt, même en l’absence de ports PCIe internes directement accessibles.

##### Outils logiciels

- **PCILeech** — Outil open source dédié aux attaques DMA, permettant la lecture et l’écriture de la mémoire RAM via un périphérique PCIe malveillant. PCILeech offre des fonctionnalités avancées telles que le dump complet de la mémoire, l’injection de code en mémoire et l’exploitation de vulnérabilités liées à l’absence ou à la mauvaise configuration des protections anti-DMA.

### Attaque cold boot

#### Techniques utilisées

L’attaque par cold boot exploite la durée de rétention des données en mémoire RAM lorsque celle-ci est exposée à de basses températures.
Cette attaque consiste à figer l’état de la mémoire RAM en la refroidissant à très basse température (environ –60 °C). À cette température, la durée de rétention des données en RAM peut atteindre plusieurs minutes, contre seulement quelques secondes à température ambiante.
Ce temps de rétention prolongé permet à un attaquant de transférer physiquement les barrettes de mémoire RAM vers un autre ordinateur. L’attaquant démarre alors ce second système sur un environnement très léger (quelques mégaoctets seulement), afin de minimiser toute réécriture en mémoire. Il est ainsi possible de copier l’intégralité du contenu de la RAM.
L’objectif principal de cette attaque est la récupération d’informations sensibles, telles que des clés de chiffrement BitLocker, des mots de passe de session ou d’autres secrets présents en mémoire.
Dans le cas où la mémoire RAM est soudée à la carte mère, le transfert physique vers un autre système n’est pas possible. L’attaquant doit alors adopter une approche différente : il lui est nécessaire de modifier certaines variables NVRAM du BIOS/UEFI afin d’empêcher l’effacement de la mémoire RAM au redémarrage, tout en conservant la capacité de démarrer sur un système d’exploitation alternatif.
Comme précédemment, l’attaquant démarre alors sur un système minimal, puis procède au dump complet de la mémoire RAM, afin d’en effectuer l’analyse à froid.

#### Présentation des outils

Pour la réalisation d’attaques de type cold boot, les auditeurs disposent des équipements suivants.

##### Équipements matériels

- **Bombe dépoussiérante**  
  Utilisée retournée, cette bombe projette le gaz qu’elle contient sous forme liquide, ce qui a pour effet d’abaisser très fortement la température des composants ciblés (environ –60 °C). Ce refroidissement rapide permet de prolonger la durée de rétention des données en mémoire RAM.

- **Ordinateur disposant de caractéristiques mémoire compatibles**  
  Un second ordinateur présentant des caractéristiques de RAM identiques ou compatibles (type, fréquence, tension) est utilisé lorsque le transfert physique de la mémoire est possible, afin de permettre la lecture du contenu mémoire.

- **Équipements de reprogrammation du firmware**  
  L’ensemble du matériel de reprogrammation du firmware (programmateurs, pinces, adaptateurs) peut être utilisé lorsque la mémoire RAM est soudée à la carte mère. Ces outils permettent notamment de modifier certaines variables NVRAM du BIOS/UEFI, afin d’empêcher l’effacement de la mémoire au redémarrage et de permettre le démarrage sur un système d’exploitation alternatif.
