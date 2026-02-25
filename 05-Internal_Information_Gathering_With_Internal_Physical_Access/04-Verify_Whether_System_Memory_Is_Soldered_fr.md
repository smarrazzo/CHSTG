# Vérifier si la mémoire système est soudée

|ID          |
|------------|
|CHSTG-INT-04|

## Résumé

Ce contrôle vise à déterminer si la mémoire système (RAM) est soudée directement sur la carte mère ou installée sous forme de modules amovibles. L'objectif est d'évaluer la remplaçabilité physique de la mémoire système.

## Objectifs du test
- Identifier si la RAM est soudée à la carte mère
- Déterminer la présence de modules mémoire amovibles
- Évaluer la remplaçabilité physique de la mémoire

## Comment tester
1. Ouvrir l'appareil selon les procédures de démontage standard.

2. Inspecter visuellement la zone mémoire sur la carte mère.

3. Déterminer si :
   - Les puces mémoire sont soudées directement sur la carte mère
   - Des modules mémoire amovibles (ex. SO-DIMM) sont présents

Exemples :

- **HP EliteBook x360 830 G8**  
![HP EliteBook x360 830 G8](imgs/HP_solder_ram.png)  
Sur le HP EliteBook x360 830 G8, la RAM est soudée à la carte mère et protégée derrière un blindage clipsé. Aucune possibilité de remplacement ou d’ajout.

- **Lenovo ThinkPad X1 Carbon Gen6**  
![Lenovo Thinkpad X1 Carbon Gen6](imgs/lenovo_Inaccesible_ram.png)  
Sur le Lenovo ThinkPad X1 Carbon Gen6, la RAM est soudée et difficile d'accès : le retrait du capot n’est pas suffisant, il est nécessaire de retirer le clavier pour accéder à la mémoire.

- **Dell Latitude 7280**  
![Dell Latitude 7280](imgs/DELL_removable_ram.png)  
Sur le Dell Latitude 7280, la RAM est immédiatement accessible et au format SO-DIMM, ce qui permet son retrait et son remplacement facilement.

4. Documenter la configuration mémoire (entièrement soudée, entièrement amovible ou configuration hybride).

## Remédiation
Non applicable.
