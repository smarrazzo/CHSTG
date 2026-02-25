# Vérifier les protections anti cold boot

|ID          |
|------------|
|CHSTG-FIRM-13|

## Résumé

Ce contrôle vise à vérifier si les protections anti cold boot sont activées dans la configuration BIOS/UEFI après avoir obtenu l'accès au micrologiciel (ex. via CHSTG-FIRM-01 ou CHSTG-FIRM-06 sans modification du firmware). L'objectif est de déterminer si les mécanismes de protection mémoire sont configurés pour atténuer les attaques par cold boot.

## Objectifs du test
- Identifier la présence de mécanismes de protection anti cold boot
- Vérifier si les fonctionnalités de protection mémoire sont activées
- Confirmer la configuration des mécanismes de protection RAM au niveau firmware

## Comment tester
1. Accéder à l'interface de configuration BIOS/UEFI (sans modifier le firmware).

2. Naviguer vers les sections avancées, chipset ou liées à la sécurité.

3. Identifier les options de configuration liées aux mécanismes de protection mémoire, telles que :
   - Chiffrement de la mémoire
   - Chiffrement RAM
   - Brouillage de la mémoire
   - Brouillage SRAM
   - Protection cold boot

4. Vérifier si ces protections sont :
   - Présentes
   - Activées
   - Configurables

5. Documenter le statut de protection et la configuration.

## Remédiation
Activer tous les mécanismes de protection mémoire disponibles (ex. chiffrement mémoire, brouillage mémoire) dans les paramètres BIOS/UEFI pour atténuer les risques d'attaque par cold boot.
