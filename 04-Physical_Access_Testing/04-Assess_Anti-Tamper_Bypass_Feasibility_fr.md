# Évaluer la faisabilité du contournement anti-effraction

|ID          |
|------------|
|CHSTG-PHY-04|

## Résumé

Ce contrôle vise à évaluer si les mécanismes anti-effraction physiques existants pourraient être contournés lorsque l'accès physique à l'appareil est disponible. L'objectif est d'évaluer la robustesse des protections mises en place et de déterminer leur résistance à une manipulation destructive ou semi-destructive.

## Objectifs du test
- Évaluer la résilience des mécanismes anti-effraction physiques
- Évaluer si les protections reposent uniquement sur des déclencheurs mécaniques ou électriques simples
- Déterminer la faisabilité globale du contournement dans des scénarios d'attaque physique réalistes

## Comment tester
1. Identifier les mécanismes anti-effraction précédemment détectés (ex. interrupteurs d'intrusion, interrupteurs de coupure, pastilles conductrices, traces d'effraction).

2. Analyser leurs caractéristiques de conception mécanique et électrique :
   - Emplacement dans le châssis
   - Dépendance à la pression mécanique ou à la continuité électrique
   - Intégration avec la logique de détection du firmware

3. Évaluer les catégories d'attaque potentielles à haut niveau :
   - Approches destructives (dommage physique au châssis tout en maintenant l'état du capteur)
   - Manipulation semi-destructive des composants de détection
   - Manipulation de la continuité électrique dans le cas de pastilles conductrices

4. Évaluer :
   - Le niveau de compétence requis
   - L'outillage requis
   - La probabilité de dommage visible
   - La probabilité de contournement réussi sans déclencher la détection

5. Documenter le niveau de faisabilité global (Faible / Moyen / Élevé).

## Remédiation
Non applicable.
