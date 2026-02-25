# Vérifier l'activation de la virtualisation

|ID          |
|------------|
|CHSTG-FIRM-16|

## Résumé

Ce contrôle vise à vérifier si les fonctionnalités de virtualisation matérielle sont activées dans la configuration BIOS/UEFI après avoir obtenu l'accès au micrologiciel (ex. via CHSTG-FIRM-01 ou CHSTG-FIRM-06 sans modification du firmware). L'objectif est de déterminer si le support de virtualisation au niveau processeur est activé.

## Objectifs du test
- Identifier la présence des fonctionnalités de virtualisation matérielle
- Vérifier si la virtualisation est activée
- Confirmer l'activation des implémentations spécifiques à la plateforme (VT-x / AMD-V)

## Comment tester
1. Accéder à l'interface de configuration BIOS/UEFI (sans modifier le firmware).

2. Naviguer vers les sections avancées, processeur ou liées au chipset.

3. Identifier les options de configuration liées à la virtualisation, telles que :
   - Technologie de virtualisation
   - Intel VT-x
   - AMD-V

4. Vérifier si ces fonctionnalités sont :
   - Présentes
   - Activées
   - Configurables

5. Documenter le statut d'activation et la configuration.

## Remédiation
Activer les fonctionnalités de virtualisation matérielle (Intel VT-x ou AMD-V) dans les paramètres BIOS/UEFI lorsque requis pour des charges de travail sécurisées basées sur la virtualisation.
