# learngitipp
Dépôt pour apprendre à utiliser git à l'ipp

## Quelques commandes principales

A taper dans un terminal relié à git

### Au moment de rejoindre un dépôt (repository)

git clone [lien récupéré dans Code/https sur github] # Crée un dossier copiant le dépôt à l'emplacement du terminal

### Gérer les modifications effectuées dans le remote

git fetch --all --prune # Le --prune permet de supprimer les branches supprimées dans le remote

gitk --all # Ouvre une interface pour voir les changements. Il faut la fermer pour effectuer les autres actions

git checkout [nom_de_la_branche_qu'on_veut_mettre_à_jour et sur laquelle on veut se mettre]

git pull # Attention, dans ce cas il peut y avoir des conflits !

### Ajouter ses propres modifications

git checkout -b [nom_de_la_nouvelle_branche] # pour créer une nouvelle branch et s'y mettre

git gui # Ouvre une interface permettant de faire des commits de manière simplifiée. Autrement :

- git add [nom du/des fichier(s) à ajouter, ou "." pour ajouter tout les changements] # Permet de stage les changements séletionnés

- git commit # Ouvre une interface où on peut mettre le nom du commit. L'interface n'est pas en mode éditable, il faut commencer par taper "a" pour entrer dans ce mode, puis echap, ":x!" pour enregistrer et quitter. Le commit des changements en statut stage est ensuite effectué.

git push # Permet d'envoyer à la branche distante les changements effectués. S'il y a un conflit entre la branche distante et locale, ce n'est pas possible (sauf avec --force, option à utiliser avec beaucoup de précaution !)

git stash # Permet de mettre de côté les derniers changements et revenir au dernier commit. On peut ensuite les réinjecter (y compris dans une autre branche) via git stash pop ou les supprimer définitivement avec git stash drop.

### Utiliser différentes branches

git merge [nom_de_la_branche_a_merger] # ajoute les commits de la branche_a_merger dans la branche actuelle. Peut créer des conflits s'il y a des changements sur les mêmes lignes. Option --no-ff pour voir qu'il y a eu un merge.

git cherry-pick [commit_tag] # permet de prendre un commit dans une autre branche et de le mettre dans l'actuelle. Dans le gitk, click droit sur un commit pour avoir l'option.

### Faire un joli arbre de commits

git rebase [nom_de_la_branche_ou_du_commit_ou_on_veut_faire_demarrer_la_branche_actuelle] # Fait démarrer la branche à un autre endroit (par exemple sur le nouveau master/main après merge d'une autre branche). !!! Attention : nécessite des push --force (car forcément conflit) qui peuvent détruire des données !!! A ne faire qu'une fois qu'on est sûr que personne ne fait de changement sur la branche (avant de merge typiquement). Option "-i" pour fusionner des commits ou en supprimer (!!! là aussi de manière difficilement réversible !!!)

git push --force # Remplace la branche distante parla branche locale, même s'il y a des conflits. !!! Attention : risque de détruire des commits !!!