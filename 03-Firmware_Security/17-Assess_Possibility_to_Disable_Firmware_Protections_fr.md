# Évaluer la possibilité de désactiver les protections firmware

|ID          |
|------------|
|CHSTG-FIRM-17|

## Résumé

Ce contrôle vise à évaluer si les protections de sécurité du micrologiciel peuvent être désactivées sans connaître le mot de passe administrateur BIOS/UEFI en modifiant directement les variables NVRAM du firmware dans un dump firmware. L'objectif est d'évaluer l'exposition des protections au niveau firmware à une manipulation directe lorsque l'accès physique au système est disponible.

## Objectifs du test
- Déterminer si les protections firmware reposent sur des variables NVRAM modifiables
- Évaluer si une modification directe des variables firmware pourrait désactiver les protections de sécurité
- Identifier l'exposition des protections telles que VT-d, IOMMU, anti-DMA ou protections mémoire au contournement au niveau firmware
- Évaluer le risque global de contournement de la configuration firmware sans authentification BIOS

## Comment tester
1. Identifier les protections de sécurité activées dans le BIOS/UEFI (ex. VT-d, IOMMU, anti-DMA, protections mémoire).

2. Évaluer si la configuration du firmware est stockée dans des variables NVRAM qui pourraient théoriquement être modifiées par manipulation du dump firmware.

3. D'après les tests empiriques et l'expérience de recherche interne, certains systèmes (ex. HP 430 G6) peuvent stocker les états de protection dans des variables telles que :
   - `IntelTechnologieOptions`
   - `S3MemoryVariable`

4. Évaluer si les protections de sécurité semblent reposer sur des variables et donc potentiellement modifiables en dehors des mécanismes d'authentification BIOS normaux.

5. Documenter :
   - Si les protections semblent basées sur la NVRAM
   - La faisabilité technique de la modification
   - Le niveau d'expertise requis
   - L'exposition globale des protections firmware à une manipulation directe

## Remédiation
Appliquer une résine époxy sur la puce BIOS/UEFI pour empêcher l'accès physique et la lecture ou l'écriture non autorisée du micrologiciel.
