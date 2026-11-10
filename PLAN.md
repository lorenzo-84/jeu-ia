# Plan : ajouter un cristal de glace

1. Ajouter dans `config.js` le type `GLACE`, sa couleur et sa rareté ; la durée de 4 secondes doit rester réglable dans `config.js`.
2. Modifier `creerObjet()` dans `jeu.js` pour créer rarement un cristal de glace, encore moins souvent qu'un cristal doré.
3. Ajouter un chronomètre de ralentissement, remis à zéro dans `demarrerPartie()`.
4. Lorsque le cristal de glace est attrapé, activer ce chronomètre dans `toucherObjet()`.
5. Dans `mettreAJour()`, ralentir la chute de tous les objets pendant le chronomètre, puis revenir automatiquement à la vitesse normale après 4 secondes.
6. Modifier `dessin.js` pour donner une apparence glacée au nouveau cristal.
7. Vérifier avec `node --check jeu.js` et tester le jeu dans le navigateur.

## Comment vérifier dans le jeu

Lancer une partie, attraper un cristal de glace, vérifier que tous les objets ralentissent pendant 4 secondes, puis vérifier qu'ils retrouvent leur vitesse normale et que la glace apparaît moins souvent que le cristal doré.