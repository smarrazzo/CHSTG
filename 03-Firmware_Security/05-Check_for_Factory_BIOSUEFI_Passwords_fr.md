# Vérifier les mots de passe BIOS/UEFI usine

|ID          |
|------------|
|CHSTG-FIRM-05|

## Résumé

Ce contrôle vise à déterminer si un mot de passe usine du fabricant existe et pourrait contourner la protection BIOS/UEFI configurée.

## Objectifs du test
- Identifier l'existence de mots de passe de secours du fabricant
- Évaluer le risque de contournement de la protection du micrologiciel
- Vérifier la robustesse de l'implémentation du mot de passe BIOS/UEFI

## Comment tester
1. S'assurer qu'un mot de passe BIOS/UEFI est configuré et actif.

2. Tenter d'accéder à l'interface BIOS/UEFI et provoquer un échec de mot de passe (si nécessaire pour obtenir un code de déverrouillage ou un hash système).

3. Noter tout code d'arrêt, code de défi ou identifiant système affiché après des tentatives d'authentification échouées.

4. Utiliser les ressources publiquement disponibles pour déterminer si un mot de passe usine ou maître existe pour le modèle d'appareil.

Exemple de ressource :
https://bios-pw.org/

5. Tenter une authentification avec tout mot de passe usine ou maître dérivé (sans modifier les paramètres du système).

6. Documenter si la protection du micrologiciel peut être contournée à l'aide d'un mot de passe fabricant.

## Remédiation
Mettre à jour le micrologiciel du système vers la dernière version et s'assurer que les mécanismes de mot de passe usine ou maître sont désactivés ou atténués lorsque le fabricant le prend en charge.
