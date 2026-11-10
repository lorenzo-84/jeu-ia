# Journal de bord

Nom et prénom : gracia de sola  lorenzo
Dépôt : https://github.com/lorenzo-84/jeu-ia
Outil utilisé (Copilot, modèle affiché) : 

Règle : tu colles ici le texte exact de tes prompts (copier-coller, pas de capture). Une entrée par défi. Ce que tu n'as pas gardé compte autant que ce que tu as gardé.

## Défi 1 - Complétion

- Commentaire ou début de code que j'ai écrit :
// compte les cristaux attrapés dans la variable cristaux
// affiche le nombre de cristaux attrapés sur l'écran de fin
```
(colle-le ici)
```

- Ce que Copilot a proposé :Commentaire 1 (dans toucherObjet) : if (objet.type === cRISTAL) { cristaux += 1; }. La suggestion contenait une faute de casse : cRISTAL n'existe pas dans le jeu, la constante s'appelle CRISTAL.Commentaire 2 (dans terminerPartie) : le code d'affichage (finCristaux.textContent = cristaux;) n'est pas venu de la complétion, je l'ai obtenu avec l'aide de Claude (chat), avec un nouvel élément fin-cristaux ajouté dans index.html.
- Ce que j'ai accepté, modifié ou refusé, et pourquoi :  Suggestion 1 : modifiée. J'ai corrigé cRISTAL en CRISTAL, sinon le jeu aurait planté (cRISTAL is not defined) dès qu'un objet est attrapé. J'ai gardé la condition objet.type === CRISTAL : seuls les cristaux cyan sont comptés, pas les cristaux dorés, ni les bombes.
Suggestion 2 : acceptée après relecture, avec le bloc CRISTAUX ajouté à l'écran de fin.
J'ai vérifié que cristaux est déclarée en haut de jeu.js (let cristaux = 0;) et remise à zéro dans demarrerPartie (cristaux = 0;).
- Comment j'ai vérifié que ça marche :
Comment j'ai vérifié que ça marche : node --check jeu.js ne signale aucune erreur. J'ai rechargé index.html, joué une partie, regardé le nombre de cristaux à l'écran de fin, puis lancé une deuxième partie pour voir qu'il repart de 0.
## Défi 2 - Ask

- Ma question (prompt exact) :Je suis en Bachelor 1, j'ai fait un peu de Go. Explique jeu.js : comment fonctionnent la boucle du jeu, la chute des objets et la détection de l'objet attrapé ? Une phrase par partie.
2 eme Comment le combo est-il remis à zéro dans jeu.js ?
```
(colle-le ici)
```

- Une affirmation de la réponse que j'ai vérifiée :Après une perte de vie : dans perdreVie, le combo et son chrono sont immédiatement remis à zéro, notamment lorsqu'une bombe est attrapée ou qu'un cristal tombe.
- Comment je l'ai vérifiée (un changement dans le code, un test dans le jeu) :j'ai ajouté console.log("perdreVie : combo avant =", combo); au début de perdreVie, ouvert la console (F12), atteint x2 avec 3 cristaux de suite, puis attrapé une bombe et raté un cristal. [A COMPLETER : ce que la console et le HUD ont montré, ex. "le message affichait combo = 3 et le HUD est repassé à x1".] J'ai ensuite retiré le console.log.
- Résultat : exacte, fausse ou incomplète :Copilot oublie que demarrerPartie remet aussi le combo à zéro, et qu'un cristal doré raté n'appelle pas perdreVie donc ne remet pas le combo à zéro.

## Défi 3 - Plan

- Mon prompt en mode Plan :

Je veux ajouter un cristal de glace, plus rare que le doré. Quand on l'attrape, tous les
objets ralentissent pendant 4 secondes, puis reprennent leur vitesse. Respecte les règles de
.github/copilot-instructions.md. Propose un plan sans modifier le code.

- Le plan est dans le fichier `PLAN.md`.
- Ce que j'ai changé dans le plan avant de le valider (étape retirée, ajoutée, contrainte) et pourquoi :
J'ai regroupé les étapes concernant le ralentissement et le retour à la vitesse normale, car elles décrivaient le même fonctionnement. J'ai ajouté la contrainte que la durée de 4 secondes doit être réglable dans `config.js`, afin de respecter l'organisation du projet. J'ai aussi ajouté une section « Comment vérifier dans le jeu » pour décrire les tests à effectuer.


## Défi 4 - Agent

- Mon prompt en mode Agent :

Applique le plan décrit dans PLAN.md.

Objectif :
Ajouter le cristal de glace, plus rare que le cristal doré, qui ralentit tous les objets pendant 4 secondes quand il est attrapé.

Contraintes :
Respecte .github/copilot-instructions.md, garde le code simple, conserve les réglages dans config.js et ne modifie pas les fichiers sans rapport.

Après les modifications, lance node --check sur chaque fichier JavaScript modifié et indique les fichiers changés.

- Fichiers que l'agent a modifiés :
`config.js`, `jeu.js`, `dessin.js`.

- Ce que j'ai relu dans les changements avant d'accepter :
J'ai vérifié que la rareté et la durée du ralentissement sont dans `config.js`, que le chronomètre est remis à zéro au début d'une partie et que le ralentissement dure 4 secondes.

- Ce que j'ai refusé, corrigé ou fait refaire :
J'ai corrigé le code car `chronoGlace` était utilisé sans être déclaré. J'ai aussi vérifié que le cristal de glace avait une couleur différente dans `dessin.js`.

- Mon deuxième prompt :

```
Objectif :
Ajouter un bouclier qui absorbe la prochaine bombe et l'afficher dans le HUD.

Contexte :
Le jeu est un jeu d'arcade spatial où le joueur attrape des cristaux qui tombent avec un panier.

Contraintes :
Le bouclier doit être obtenu en attrapant un nouvel objet rare et absorber une seule bombe. Sa rareté doit être réglable dans `config.js`. Respecte les règles de `.github/copilot-instructions.md`.

Format attendu :
Modifie les fichiers nécessaires, lance node --check sur les fichiers JavaScript modifiés et explique les tests à effectuer.
```

- Prompt court après la mise à jour des instructions :

```
Relis .github/copilot-instructions.md et vérifie que les changements du bouclier respectent bien le thème spatial néon et les règles du projet. Corrige uniquement ce qui ne les respecte pas, puis lance node --check.
```

- Fichiers modifiés pour le bouclier :
`config.js`, `jeu.js`, `dessin.js`, `index.html`, `style.css` et `.github/copilot-instructions.md`.

- Ce que j'ai relu :
J'ai vérifié que le HUD affiche « BOUCLIER ACTIF » après l'obtention et « BOUCLIER VIDE » après l'utilisation. Le test doit être fait après avoir attrapé le bouclier : la bombe protégée ne retire pas de vie, puis la bombe suivante retire bien une vie.

- Ce que j'ai refusé, corrigé ou fait refaire :
J'ai corrigé le traitement de la bombe en séparant l'absorption dans une fonction `absorberBombe`. Cela garantit qu'un bouclier actif est consommé sans appeler `perdreVie`; j'ai aussi remis la rareté temporairement augmentée à `0.01` après le test.

- Mon jeu après l'agent :
Le jeu démarre dans le navigateur et le HUD affiche l'état du bouclier.

- Commits réalisés :
`defi 4 : cristal de glace`
`defi 4 : bouclier`

## Défi 5 - Pull request et revue

- Lien de ma pull request : à compléter après la création sur GitHub.
- Commentaire de la revue Copilot que j'ai traité (le texte) : à copier depuis la revue GitHub.
- Ma décision (corrigé ou refusé) et pourquoi : à compléter après la revue.
- Lien de mon jeu publié : à compléter après l'activation de GitHub Pages.

## Bilan (3 lignes maximum)

- Ce que l'assistant a fait mieux ou plus vite que moi :
Il m'a aidé à organiser le plan et à relier la configuration, la logique du jeu et l'affichage.
- Ce qu'il a mal fait ou ce que j'ai dû corriger :
Le bouclier n'était pas assez facile à tester et j'ai dû vérifier son fonctionnement avec une probabilité temporairement augmentée.
- Ce que je ne lui laisserais pas faire :
Je ne lui laisserais pas fusionner une pull request ou publier le jeu sans relire les changements et tester le résultat.
