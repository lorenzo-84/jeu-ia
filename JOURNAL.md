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

```
(colle-le ici)
```

- Le plan est dans le fichier `PLAN.md`.
- Ce que j'ai changé dans le plan avant de le valider (étape retirée, ajoutée, contrainte) et pourquoi :

## Défi 4 - Agent

- Mon prompt en mode Agent :

```
(colle-le ici)
```

- Fichiers que l'agent a modifiés :
- Ce que j'ai relu dans les changements avant d'accepter :
- Ce que j'ai refusé, corrigé ou fait refaire :
- Mon jeu après l'agent (une phrase) :

## Défi 5 - Pull request et revue

- Lien de ma pull request :
- Commentaire de la revue Copilot que j'ai traité (le texte) :
- Ma décision (corrigé ou refusé) et pourquoi :
- Lien de mon jeu publié :

## Bilan (3 lignes maximum)

- Ce que l'assistant a fait mieux ou plus vite que moi :
- Ce qu'il a mal fait ou ce que j'ai dû corriger :
- Ce que je ne lui laisserais pas faire :
