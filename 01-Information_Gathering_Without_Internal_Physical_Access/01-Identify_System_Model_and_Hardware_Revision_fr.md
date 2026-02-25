# Identifier le modèle système et la révision matérielle

|ID          |
|------------|
|CHSTG-INFO-01|

## Résumé

Ce contrôle vise à identifier le modèle système exact et la révision matérielle en utilisant uniquement les informations physiquement visibles sur l'appareil. L'objectif de cette étape est strictement l'identification et la collecte des références matérielles qui seront utilisées dans les phases d'analyse ultérieures.

## Objectifs du test
- Identifier le fabricant et la famille de produits à partir des marquages externes
- Déterminer le modèle système exact et la variante
- Déterminer la référence carte mère associée au modèle d'appareil
- Collecter les identifiants matériels pour les étapes d'investigation futures

## Comment tester
1. Effectuer une inspection visuelle externe de l'appareil :
   - Logo du fabricant
   - Nom de la série produit
   - Numéro de modèle
   - Numéro de service / numéro de série
   - Étiquettes réglementaires
   - Étiquettes d'actif ou autocollants code-barres

2. Noter tous les identifiants exactement tels qu'écrits.

3. Utiliser les identifiants collectés dans les moteurs de recherche pour déterminer la référence produit exacte.

4. À partir du nom de modèle confirmé, rechercher le modèle avec le mot-clé **carte mère** (motherboard) pour identifier la référence carte mère associée à l'appareil.

Exemple :

Pour chaque appareil, effectuer une recherche combinant le nom du modèle avec le mot-clé `Motherboard` pour aider à identifier la référence carte mère réelle :

- ASUS R753UX
![ASUS-R753UX](img/ASUS-R753UX.png)  
  Recherche : `ASUS R753UX Motherboard`  
Carte mère générique utilisée dans plusieurs modèles, également connue sous le nom **X756UXM**, avec numéro de pièce **DAXK9FMB6C0**.

- HP 430 G6
![HP-430-G6](img/Ex_HP-probook-430-G6.png)  
  Recherche : `HP 430 G6 Motherboard`  
  Le résultat permet de trouver la référence carte mère spécifique (ex. **DA0X8IMB8E0**).

- Samsung NP754XGK
  Recherche : `Samsung NP754XGK Motherboard`
  Vous pouvez généralement identifier l'étiquette carte mère (ex. **TITAN4 NB6099C_PCB_MB_MP1.0**).

Cette approche permet de confirmer et documenter de manière fiable à la fois le modèle d'appareil et sa référence carte mère correspondante.

5. Documenter le modèle confirmé et la référence carte mère pour une utilisation ultérieure dans les étapes d'analyse matérielle suivantes.

## Remédiation
Non applicable.
