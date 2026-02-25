# Évaluer l'accès BIOS/UEFI niveau administrateur

|ID          |
|------------|
|CHSTG-FIRM-02|

## Résumé

Ce contrôle vise à déterminer si les paramètres de configuration BIOS/UEFI peuvent être modifiés sans authentification. L'objectif est de vérifier la présence d'un mot de passe administrateur protégeant les modifications de configuration du micrologiciel.

## Objectifs du test
- Identifier si les paramètres BIOS/UEFI peuvent être modifiés sans authentification
- Vérifier la présence d'un mot de passe administrateur
- Déterminer si les modifications de configuration sont correctement restreintes

## Comment tester
1. Mettre le système sous tension.

2. Accéder à l'interface de configuration BIOS/UEFI au démarrage.

3. Tenter de modifier un paramètre de configuration non critique (sans enregistrer les modifications).

4. Observer le comportement du système :
   - Si les modifications sont autorisées sans authentification → pas de protection administrateur
   - Si une demande de mot de passe apparaît avant la modification → protection administrateur activée

5. Vérifier si un mot de passe est requis :
   - Pour accéder aux menus de configuration
   - Ou spécifiquement lors de la tentative de modification des paramètres

6. Documenter si la modification du micrologiciel est protégée par un mot de passe.

## Remédiation
Configurer un mot de passe administrateur BIOS/UEFI pour empêcher la modification non autorisée des paramètres du micrologiciel.
