# Vérifier le statut de protection anti-DMA Thunderbolt/USB4

|ID          |
|------------|
|CHSTG-FIRM-09|

## Résumé

Ce contrôle vise à vérifier si les protections anti-DMA Thunderbolt et/ou USB4 sont activées dans la configuration BIOS/UEFI après avoir obtenu l'accès au micrologiciel (ex. via CHSTG-FIRM-01 ou CHSTG-FIRM-06 sans modification du firmware). L'objectif est de déterminer si les protections contre l'accès DMA non autorisé via les interfaces externes haute vitesse sont correctement configurées.

## Objectifs du test
- Identifier la présence de mécanismes de protection anti-DMA Thunderbolt
- Identifier la présence de mécanismes de protection DMA USB4
- Vérifier si ces protections sont activées
- Confirmer la configuration au niveau firmware des atténuations DMA spécifiques aux interfaces

## Comment tester
1. Accéder à l'interface de configuration BIOS/UEFI (sans modifier le firmware).

2. Naviguer vers les sections avancées, sécurité ou configuration Thunderbolt/USB.

3. Identifier les options de configuration liées à la protection DMA, telles que :
   - Protection DMA USB4
   - Protection DMA Thunderbolt
   - Niveau de sécurité Thunderbolt
   - Protection Thunderbolt avant démarrage

4. Vérifier si ces protections sont :
   - Présentes
   - Activées
   - Configurables

5. Documenter le statut de protection et tout paramètre configurable.

## Remédiation
Activer tous les mécanismes de protection DMA Thunderbolt et USB4 disponibles dans les paramètres BIOS/UEFI pour atténuer les attaques d'accès direct à la mémoire non autorisées via les interfaces externes haute vitesse.
