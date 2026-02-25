# Évaluer le démarrage automatique complet

|ID          |
|------------|
|CHSTG-BOOT-03|

## Résumé

Ce contrôle vise à déterminer si le système démarre automatiquement jusqu'à l'écran de connexion sans exiger aucune interaction utilisateur, telle qu'un code PIN de déchiffrement de disque ou une authentification pré-démarrage.

## Objectifs du test
- Identifier si le système effectue un démarrage entièrement automatique
- Détecter l'absence de mécanismes d'authentification pré-démarrage
- Déterminer si une interaction utilisateur est requise avant l'écran de connexion

## Comment tester
1. S'assurer que le système est arrêté.

2. Mettre l'appareil sous tension.

3. Observer le processus de démarrage :
   - Vérifier si un écran d'authentification pré-démarrage apparaît (PIN, mot de passe, carte à puce, etc.)
   - Vérifier si les identifiants de déchiffrement du disque sont requis

4. Déterminer le comportement du système :
   - Si le système atteint l'écran de connexion du système d'exploitation sans aucune interaction utilisateur → démarrage automatique
   - Si des identifiants sont requis avant l'écran de connexion → démarrage protégé

5. Documenter le comportement observé.

## Remédiation
Activer l'authentification pré-démarrage (par exemple chiffrement complet du disque avec PIN ou mot de passe pré-démarrage) pour empêcher l'accès non autorisé au système pendant le démarrage.
