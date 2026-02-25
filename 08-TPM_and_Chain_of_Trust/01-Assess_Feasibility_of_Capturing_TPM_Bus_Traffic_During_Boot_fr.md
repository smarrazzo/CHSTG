# Évaluer la faisabilité de capturer le trafic du bus TPM pendant le démarrage

|ID          |
|------------|
|CHSTG-TPM-01|

## Résumé

Le module de plateforme sécurisée (TPM) est responsable du stockage et de la libération sécurisés des clés de chiffrement, telles que la clé maîtresse de volume BitLocker (VMK). Dans de nombreuses configurations, notamment les modes « TPM uniquement », le module libère automatiquement la clé au processeur via un bus physique (SPI ou I2C) pendant le processus de démarrage. Ce contrôle évalue le risque d'interception de ces données sensibles en écoutant physiquement le bus de communication à l'aide d'analyseurs logiques. Cette attaque est particulièrement efficace car la communication entre le TPM et le processeur est souvent non chiffrée.

## Objectifs du test
- Identifier le type de bus physique (SPI, I2C ou LPC) utilisé par le TPM.
- Capturer avec succès les signaux numériques pendant l'autotest de mise sous tension (POST) et la phase de démarrage du système d'exploitation.
- Déterminer si le trafic capturé contient du matériel exploitable, tel que des clés de chiffrement en clair.

## Comment tester
Ce test nécessite un accès physique interne à la carte mère pour placer des sondes sur les lignes de communication.

### Configuration matérielle
1.  **Analyseur logique :** Utiliser un analyseur logique avec une fréquence d'échantillonnage d'au moins 100 MHz pour s'assurer que les signaux SPI haute vitesse sont capturés avec précision.
2.  **Outils de sondage :** Utiliser des sondes à ressort (ex. **PCBite**) pour un contact sans main destructif avec les broches de puces ou pastilles de test.
3.  **Identification des signaux :**
    * **Bus SPI :** Localiser et sonder les lignes **MISO** (Master In Slave Out), **MOSI** (Master Out Slave In) et **CLK** (horloge).
    * **Chip Select (CS) :** Bien que non strictement requis pour le décodage, sonder la ligne CS aide à différencier les composants sur un bus partagé.
4.  **Stratégie de bus partagé :** Comme le bus SPI est souvent partagé entre le TPM, le BIOS/UEFI et le contrôleur embarqué (EC), vous pouvez capturer le trafic TPM en sondant les broches de la puce BIOS ou EC si le TPM est physiquement inaccessible (ex. situé au verso de la carte). Utiliser le signal CS du BIOS pour identifier le trafic non-BIOS (le TPM est actif lorsque le CS du BIOS est haut/inactif).

Exemples:

- **HP Probook 430 G6**  
  ![alt text](tpm/TPM_HP_430_G6.png)  
  Ici, les sondes sont placées directement autour de la puce TPM. L’espace autour de la puce est suffisant pour positionner les sondes de manière stable, ce qui permet d’obtenir un signal propre et donc exploitable.

- **Dell Latitude 5420**  
  ![alt text](tpm/TPM_Dell.png)  
  Dans certains cas, les sondes ne tiennent pas bien en place ou le signal capturé n’est pas suffisamment propre pour une analyse exploitable. Une alternative consiste alors à souder des fils très fins directement sur les lignes du bus SPI afin d’assurer une connexion fiable et d’obtenir un signal optimal pour le décodage.

- **Samsung NP754XGK**  
  ![alt text](tpm/SAMSUNG_bios_TPM.png)  
  Sur ce modèle, la puce BIOS et la puce TPM sont très proches l’une de l’autre, ce qui rend le placement des sondes autour du TPM particulièrement difficile. Cependant, comme les deux circuits partagent le même bus SPI, il est possible d’intercepter le trafic TPM via les broches de la puce BIOS, facilitant ainsi la capture du signal sans avoir à accéder directement au TPM.  
  ![alt text](tpm/TPM_SAMSUNG.png)


### Exécution logicielle
1.  **Configurer l'analyseur :** Régler le logiciel de l'analyseur logique pour déclencher sur les premières transitions des lignes CLK ou CS.
2.  **Mise sous tension :** Démarrer le système cible.
3.  **Capture et décodage :** Utiliser les décodeurs SPI/I2C dans le logiciel de l'analyseur pour convertir les formes d'onde brutes en données hexadécimales.

## Remédiation
- **Authentification pré-démarrage :** Configurer le chiffrement disque (ex. BitLocker) pour exiger un **code PIN** ou une clé de démarrage en plus du TPM. Cela empêche le TPM de libérer la clé maîtresse sur le bus tant que l'utilisateur n'a pas été authentifié avec succès.
- **Chiffrement des paramètres TPM :** Si pris en charge par le matériel et le système d'exploitation, activer le chiffrement des paramètres TPM 2.0 pour protéger la sensibilité des données transitant sur le bus.
- **Protection physique :** S'assurer que le châssis est sécurisé par des mécanismes inviolables pour détecter l'accès interne non autorisé.
