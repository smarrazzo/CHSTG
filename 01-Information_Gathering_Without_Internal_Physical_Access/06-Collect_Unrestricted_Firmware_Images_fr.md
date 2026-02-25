# Collecter les images de micrologiciel non restreintes

|ID          |
|------------|
|CHSTG-INFO-06|

## Résumé

Ce contrôle vise à identifier l'existence de versions de micrologiciel non restreintes ou de méthodes documentées permettant la suppression de mot de passe. L'objectif est de préparer l'analyse future en déterminant si les restrictions d'accès peuvent être contournées à l'aide de techniques documentées publiquement, sans interagir physiquement avec l'appareil.

## Objectifs du test
- Identifier les versions de micrologiciel modifiées ou non restreintes
- Identifier les méthodes documentées de suppression de mot de passe
- Évaluer les risques associés à l'utilisation de micrologiciels non officiels
- Privilégier les solutions basées sur le micrologiciel d'origine de l'appareil

## Comment tester
1. Utiliser le modèle d'appareil exact identifié lors du test CHSTG-INFO-01.

2. Effectuer des recherches en ligne en combinant le modèle avec des mots-clés tels que :
   - bios unlock (déverrouillage BIOS)
   - password removal (suppression de mot de passe)
   - supervisor password reset (réinitialisation mot de passe superviseur)
   - unlocked bios
   - modded firmware (micrologiciel modifié)

3. Identifier deux approches possibles :
   - Images de micrologiciel modifiées supprimant les restrictions
   - Procédures documentées permettant la suppression de mot de passe avec le micrologiciel d'origine

4. Prioriser les méthodes documentées de suppression par rapport aux images de micrologiciel modifiées, car le micrologiciel modifié peut ne pas correspondre exactement à la révision matérielle et peut introduire des risques.

Exemple :

**Dell :**
- Pour les BIOS protégés par le hash 8FC8, il est possible de modifier la séquence suivante dans le dump : remplacer `00 FD AA` par `00 FD 00`. Cela active le mode Manufacturing et supprime le Service Tag, dont découle le hash du mot de passe, ce qui a pour effet de désactiver le mot de passe.

**HP :**
 - Pour les systèmes HP ProBook, il existe des méthodes documentées permettant de réinitialiser ou supprimer le mot de passe BIOS :
   https://gist.github.com/schorschii/752b3a06f7bc3b33ce7b65ff22c27337

5. Documenter les techniques identifiées et les risques associés pour une utilisation ultérieure.

## Remédiation
Non applicable.
