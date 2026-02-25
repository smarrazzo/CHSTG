# Évaluer l'accès BIOS/UEFI niveau utilisateur

|ID          |
|------------|
|CHSTG-FIRM-01|

## Résumé

Ce contrôle vise à déterminer si les informations de configuration BIOS/UEFI peuvent être consultées sans authentification. L'objectif est de vérifier si un accès en lecture seule est possible et si les paramètres liés à la sécurité peuvent être visualisés sans identifiants.

## Objectifs du test
- Identifier si le paramétrage BIOS/UEFI est accessible sans authentification
- Déterminer si les paramètres de configuration sont lisibles sans identifiants
- Vérifier la visibilité des paramètres de sécurité (anti-effraction, anti-DMA, etc.)

## Comment tester
1. Mettre le système sous tension.

2. Accéder à l'interface de configuration BIOS/UEFI au démarrage.

3. Observer si une authentification est requise avant d'accéder aux menus de configuration.

4. Si l'accès est accordé sans authentification :
   - Parcourir les sections liées à la sécurité
   - Identifier la visibilité des paramètres tels que :
     - Mécanismes anti-effraction
     - Protections anti-DMA
     - Configuration Secure Boot
     - Configuration de l'ordre de démarrage

5. Documenter si :
   - L'accès est non restreint
   - L'accès est en lecture seule
   - Une authentification est requise

## Remédiation
Configurer un mot de passe administrateur BIOS/UEFI pour restreindre l'accès non autorisé aux paramètres de configuration du micrologiciel.
