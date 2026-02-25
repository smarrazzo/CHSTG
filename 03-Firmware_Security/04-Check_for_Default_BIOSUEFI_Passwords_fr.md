# Vérifier les mots de passe BIOS/UEFI par défaut

|ID          |
|------------|
|CHSTG-FIRM-04|

## Résumé

Ce contrôle vise à déterminer si le mot de passe BIOS/UEFI configuré sur le système correspond à un mot de passe par défaut ou faible (ex. « 123456 », « admin », etc.).

## Objectifs du test
- Identifier l'utilisation de mots de passe BIOS/UEFI par défaut
- Identifier l'utilisation de mots de passe faibles ou facilement devinables
- Évaluer la solidité de la protection d'accès au micrologiciel

## Comment tester
1. S'assurer qu'un mot de passe BIOS/UEFI est configuré (comme identifié dans les tests précédents).

2. Au démarrage du système, accéder à l'interface BIOS/UEFI.

3. Tenter une authentification avec des identifiants par défaut courants tels que :
   - 123456
   - admin
   - password
   - Nom du fabricant

4. Observer le comportement du système :
   - Si l'accès est accordé avec un mot de passe courant/par défaut → configuration non sécurisée
   - Si l'accès est refusé → le mot de passe n'est pas par défaut (ou pas faible)

5. Documenter si un mot de passe par défaut ou faible est utilisé.

## Remédiation
Configurer un mot de passe BIOS/UEFI fort et unique qui ne soit pas basé sur des valeurs par défaut ou facilement devinables.
