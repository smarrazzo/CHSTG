# Identifier les points d'accès au bus SPI du TPM

|ID          |
|------------|
|CHSTG-INT-15|

## Résumé

Ce contrôle vise à identifier les points d'accès potentiels au bus de communication du TPM (SPI ou I2C), soit par revue de la documentation soit par analyse physique des signaux. L'objectif est de déterminer si l'interface de communication du TPM est exposée ou accessible au niveau matériel.

## Objectifs du test
- Identifier le type d'interface de communication du TPM (SPI ou I2C)
- Localiser les points d'accès potentiels au bus sur la carte mère
- Évaluer l'exposition des traces de communication du TPM
- Évaluer la faisabilité de l'accès physique aux signaux

## Comment tester
1. Identifier la référence exacte de la puce TPM (depuis CHSTG-INT-14).

2. Consulter la fiche technique de la puce, si disponible, pour déterminer :
   - Le type d'interface de communication (SPI ou I2C)
   - La configuration des broches
   - Les noms des signaux (CLK, MOSI, MISO, CS, SDA, SCL, etc.)

3. Inspecter la carte mère pour localiser :
   - Les traces de signaux correspondantes
   - Les pastilles de test
   - Les connecteurs non peuplés
   - Les vias accessibles

4. Si une observation des signaux est autorisée dans le cadre du mandat, évaluer si le sondage pourrait théoriquement être réalisé à l'aide de :
   - Systèmes de sondes à ressort (ex. PCBite)
   - Analyseurs logiques avec bande passante supérieure à 100 MHz (ex. Saleae, DSLogic)

5. Documenter :
   - Le type de bus identifié
   - L'emplacement des points d'accès potentiels
   - Le niveau d'accessibilité physique
   - L'évaluation globale de l'exposition (Faible / Moyen / Élevé)

## Remédiation
Appliquer une résine époxy sur les composants sensibles et les traces de bus exposées pour empêcher le sondage physique et l'accès non autorisé aux signaux.
