# Identifier le boîtier des puces Firmware / EC

|ID          |
|------------|
|CHSTG-INT-11|

## Résumé

Ce contrôle vise à identifier le type de boîtier physique exact de la puce de micrologiciel BIOS/UEFI et de la puce du contrôleur embarqué (EC), si présente. L'objectif est de déterminer le format de boîtier des puces à des fins d'analyse matérielle.

## Objectifs du test
- Identifier le type de boîtier de la puce BIOS/UEFI
- Identifier le type de boîtier de la puce du contrôleur embarqué (EC)
- Documenter les caractéristiques du facteur de forme physique

## Comment tester
1. Ouvrir l'appareil selon les procédures de démontage standard.

2. Localiser la puce de micrologiciel BIOS/UEFI sur la carte mère.

3. Inspecter visuellement la puce et déterminer son type de boîtier, tel que :
   - SOIC-8
   - TSOP-8
   - WSON
   - QFN8
   - Autres formats de boîtier

Exemples de types de boîtiers :

- **SOIC-8**  
![SOIC-8](imgs/BIOS_SOIC-8.png)  
Exemple : puce BIOS Winbond 25Q128 au format SOIC-8. Ce boîtier est facilement reconnaissable à sa forme rectangulaire et à ses pattes latérales (8 broches, 4 de chaque côté).

- **QFN8 / WSON8**  
![BIOS QFN8/WSON8](imgs/BIOS-QFN8.png)  
Exemple : puce BIOS Winbond 25Q256 au format QFN8/WSON8.
![EC QFN8/WSON8](imgs/EC_QFN8.png)  
Exemple : puce EC Winbond 25Q256 au format QFN8/WSON8.


4. Localiser la puce du contrôleur embarqué (EC), si présente.

5. Inspecter visuellement la puce EC et déterminer son type de boîtier.

6. Documenter les types de boîtier identifiés pour les puces firmware et EC.

## Remédiation
Non applicable.
