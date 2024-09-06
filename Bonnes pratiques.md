# Quelques bonnes pratiques sur git

Git est un langage qui permet principalement de versionner son code, et de travailler à plusieurs sur un même projet.

## Le versionnage du code

L'intérêt de versionner son code est de pouvoir revenir à un état antérieur facilement (après une erreur par exemple), et de pouvoir déterminer ce qui a changé entre deux versions.

### Créer les commits

Afin de rendre visible les changements apportés à chaque étape du code, l'important est de bien séparer et nommer ces étapes.
- **Bien séparer les commits** veut dire mettre à l'intérieur d'un commit uniquement des changements liés entre eux, et d'associer à chaque étape un nouveau commit. Cette séparation aide ensuite à mieux les nommer, étape essentielle pour arriver à comprendre les changements apportés (notamment dans le gitk).
- **Nommer correctement les commits** n'est pas toujours si simple : il faut que le nom suffise à comprendre ce qu'il y a dans le commit, tout en restant court pour permettre de le lire très rapidement (40 signes maximum). Souvent, les commencer avec un verbe ("Nomme", "Crée", "Calcule" ...) est une bonne idée.

### Créer les branches

- **Le contenu d'une branche doit être homogène**, et assurer le traitement d'un sujet du début à la fin. Un nom clair permet de voir facilement cet objectif.
- Une fois que la branche a atteint son objectif, elle a alors vocation la plupart du temps à **être mergée** dans la branche principale (main/master), puis supprimée, afin de ne pas multiplier sans raison les branches actives et de bien repérer ces dernières.

## Le travail en équipe

Git est un outil parfaitement adapté pour être plusieurs à travailler sur un même code, mais il est important de faire attention à l'impact qu'a un changement sur les autres.

- **Bien expliquer tout ce que l'on fait** : pour que les autres contributers puissent suivre et aider les développements, il est important d'expliquer à tous les niveaux ce qui est fait : dans le code, avec les commentaires, au niveau des commits (il est possible de sauter des lignes après le titre du commit pour expliquer plus longuement ce qu'il fait), et au niveau des branches, en cas d'utilisation de Pull Request dans GitHub/GitLab. Ces dernières correspondent à des endroits où les branches sont décrites, et où une discussion peut avoir lieu entre les différents contributeurs et/ou le reviewer, pour déterminer infine du fait de merger cette branche dans la branche principale.

- **Faire un arbre compréhensible**, c'est-à-dire où l'ordre d'application des branches et commits est clair (dans un gitk), et où ces derniers sont facilement compréhensibles. Ceci passe dans les grands projets par l'utilisation de rebase avant les merge. Mais,

- **Faire attention avec les réécritures d'historique** : ces dernières (rebase, cherry-pick, résolution de conflits dans un merge, suivis de push --force) permettent de modifier la forme de l'arbre pour le rendre plus facilement lisible, mais sont aussi l'un des rares cas où il est possible de perdre de l'information sur git. Ne pas hésiter à faire des tests sur d'autres branches pour vérifier le fonctionnement de ces outils, à appeler des personnes plus expérimentées, et à annuler ces procédures (git rebase --abort par exemple) si vous sentez qu'elles vous échappe. Et surtout, toujours vérifier que rien n'est perdu en local avant de faire un push --force, qui enlève la possibilité de revenir à l'état de l'origine.

- **Ne pas hésiter à communiquer avec vos collègues** : que ce soit pour annoncer un merge, témoigner d'un problème ou demander si personne n'a de modification en cours pour faire une réécriture d'historique, le mieux est encore de vérifier auprès des autres contributeurs quelle est la meilleure marche à suivre.