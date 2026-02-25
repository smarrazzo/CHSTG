# Vérifier l'activation de l'IOMMU

|ID          |
|------------|
|CHSTG-FIRM-11|

## Résumé

Ce contrôle vise à vérifier si les mécanismes de protection basés sur l'IOMMU sont activés dans la configuration BIOS/UEFI après avoir obtenu l'accès au micrologiciel (ex. via CHSTG-FIRM-01 ou CHSTG-FIRM-06 sans modification du firmware). L'objectif est de déterminer si l'isolation DMA matérielle est correctement configurée.

## Objectifs du test
- Identifier la présence des fonctionnalités liées à l'IOMMU
- Vérifier si l'IOMMU est activé
- Confirmer l'activation des implémentations spécifiques à la plateforme (VT-d / AMD-Vi)

## Comment tester
1. Accéder à l'interface de configuration BIOS/UEFI (sans modifier le firmware).

2. Naviguer vers les sections avancées, chipset, processeur ou liées à la sécurité.

3. Identifier les options de configuration liées à l'IOMMU, telles que :
   - IOMMU
   - Intel VT-d
   - AMD-Vi

4. Vérifier si ces protections sont :
   - Présentes
   - Activées
   - Configurables

5. Documenter le statut d'activation et la configuration.

## Remédiation
Activer l'IOMMU (Intel VT-d ou AMD-Vi) dans les paramètres BIOS/UEFI pour appliquer l'isolation DMA au niveau matériel.
