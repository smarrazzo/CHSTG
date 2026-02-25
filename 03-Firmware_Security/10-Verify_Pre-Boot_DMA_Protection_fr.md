# Vérifier la protection DMA avant démarrage

|ID          |
|------------|
|CHSTG-FIRM-10|

## Résumé

Ce contrôle vise à vérifier si les mécanismes de protection DMA avant démarrage sont activés dans la configuration BIOS/UEFI après avoir obtenu l'accès au micrologiciel (ex. via CHSTG-FIRM-01 ou CHSTG-FIRM-06 sans modification du firmware). L'objectif est de déterminer si les protections DMA sont appliquées avant le chargement du système d'exploitation.

## Objectifs du test
- Identifier la présence de mécanismes de protection DMA avant démarrage
- Vérifier si la protection DMA avant démarrage est activée
- Confirmer l'application des restrictions DMA avant le démarrage du système d'exploitation

## Comment tester
1. Accéder à l'interface de configuration BIOS/UEFI (sans modifier le firmware).

2. Naviguer vers les sections avancées ou liées à la sécurité.

3. Identifier les options de configuration liées à la protection DMA avant démarrage, telles que :
   - Protection DMA avant démarrage
   - Protection DMA (pré-OS)
   - Protection Thunderbolt avant démarrage (le cas échéant)

4. Vérifier si ces protections sont :
   - Présentes
   - Activées
   - Configurables

5. Documenter le statut de protection et la configuration.

## Remédiation
Activer la protection DMA avant démarrage dans les paramètres BIOS/UEFI pour s'assurer que les mécanismes d'atténuation DMA sont appliqués avant le chargement du système d'exploitation.
