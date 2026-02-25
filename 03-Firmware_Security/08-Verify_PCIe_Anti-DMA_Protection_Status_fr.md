# Vérifier le statut de protection anti-DMA PCIe

|ID          |
|------------|
|CHSTG-FIRM-08|

## Résumé

Ce contrôle vise à vérifier si les protections anti-DMA PCIe sont activées dans la configuration BIOS/UEFI après avoir obtenu l'accès au micrologiciel (ex. via CHSTG-FIRM-01 ou CHSTG-FIRM-06 sans modification du firmware). L'objectif est de déterminer si les protections contre l'accès DMA non autorisé sont correctement configurées.

## Objectifs du test
- Identifier la présence de mécanismes de protection anti-DMA
- Vérifier le statut (activé/désactivé) des protections DMA PCIe
- Confirmer la configuration au niveau firmware des fonctionnalités d'atténuation DMA

## Comment tester
1. Accéder à l'interface de configuration BIOS/UEFI (sans modifier le firmware).

2. Naviguer vers les sections avancées ou liées à la sécurité.

3. Identifier les options de configuration liées à la protection DMA, telles que :
   - IOMMU
   - Intel VT-d
   - AMD-Vi
   - Protection anti-DMA
   - Protection DMA
   - Protection DMA avant démarrage

4. Vérifier si ces protections sont :
   - Présentes
   - Activées
   - Configurables

5. Documenter le statut de protection et tout paramètre configurable.

## Remédiation
Activer tous les mécanismes de protection DMA PCIe disponibles dans les paramètres BIOS/UEFI (ex. IOMMU, VT-d, AMD-Vi, protection DMA avant démarrage) pour atténuer les attaques d'accès direct à la mémoire non autorisées.
