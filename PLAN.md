# Plan : ajouter un cristal de glace

1. Ajouter dans `config.js` le type `GLACE`, sa couleur, sa rareté et la durée du ralentissement.
2. Modifier `creerObjet()` dans `jeu.js` pour créer rarement un cristal de glace, encore moins souvent qu'un cristal doré.
3. Ajouter un chronomètre de 4 secondes remis à zéro dans `demarrerPartie()`.
4. Lorsque le cristal de glace est attrapé, activer ce chronomètre dans `toucherObjet()`.
5. Pendant le chronomètre, ralentir la chute de tous les objets dans `mettreAJour()`.
6. Après 4 secondes, laisser les objets reprendre leur vitesse normale.
7. Modifier `dessin.js` pour donner une apparence glacée au nouveau cristal.
8. Vérifier avec `node --check jeu.js` et tester le jeu dans le navigateur.