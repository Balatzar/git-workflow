# Workflow

Voilà quelques règles à suivre pour bien travailler en groupe, ne pas avancer trop vite sans impliquer le groupe, limiter les conflits et autres.

N'hésitez pas à changer des choses si vous avez des idées pour collaborer plus efficacement !


## GIT !

Git est extrêmement important pour travailler en groupe. Voilà un workflow pour qu'on ne se marche pas sur les pieds et qu'on travaille bien tous ensemble.

*- Maintenir `master` deployable* :

Faire en sorte que la branche `master` ne soit composée que de features qui soient deployables, c'est-à-dire rien d'expérimental, aucun essai. Uniquement du code qui serait montrable en présentation au client, ou même déployé sur internet.


*- Utiliser la branche `dev` comme branche principale* :

On utilise la branch `dev` comme branche de développement. On ne peut envoyer du code sur `dev` qu'avec des pull request (voir point suivant).


*- Développer sur une branche créée pour la feature* :

Par exemple si je développe une feature qui va permettre aux utilisateurs d'éditer leur profil, je créé une branche `bal/edit_user` (début de mon nom/nom de la feature) et je développe toute ma feature dessus.


*- Application d'un Pull Request* :

Une fois le travail merge sur la branch [nom de la branch] :
`git request-push origin [nom de la branch]`


#### /!\ En cas d'erreur de branche :
```
// Cas: si je commence à développer sur dev mais que je n'ai pas encore commit, je fais

git checkout -b [mon nom]/[ma feature]
    // pour créer une branche et aller dessus avec mes changements
    // une fois sur ma branche je fais mes commit normalement (commiter souvent
    // pour pouvoir revenir à l'endroit précis où ça bug en cas de problème)
    // quand j'ai fini je retourne dans dev, je pull les derniers changements
git pull
    // je retourne dans ma branche et j'y merge dev
git merge dev
```

##### /!\ Il est important de toujours créer une nouvelle branche à partir de la branche `dev` updatée et de régulièrement puller `dev` et la merger dans notre branche perso pour limiter le nombre final de conflits.

#### C'est toujours à celui qui créé la pull request (PR) de gérer les conflits avec dev

Une fois que tous les conflits sont réglés, je vais sur GitHub et je créé une PR
[img]: http://i.imgur.com/iKvZD86.png
![text][img]

Et je choisis `dev` comme la base et ma branch comme compare
[img2]: http://i.imgur.com/CnSisZ5.png
![text][img2]

## Git tips

Cette façon de travailler fait que le repo reste bien organisé et surtout personne ne peut avancer
énormément sur le projet sans impliquer les autres. Si quelqu'un fait une PR, elle doit forcément être
validée par d'autres personnes qui devront relire et comprendre le code. Celles-ci peuvent faire des
commentaires et poser des questions avant de valider la PR.

*Tout le gitage et le codage se fait en anglais* :^) : Cela concerne tous les messages de commit, commentaires dans les pull request, ... (Autant s'entrainer maintenant !)

Tous les messages de commit doivent commencer par une majuscule, contenir moins de 50 caractères et ne terminer par *aucune ponctuation*.
L'utilisation de la forme impérative est le plus courant (Improve style *instead of* Improving style).
Il est possible de commenter son commit avec plus de texte en faisant `git commit`, cela ouvre votre éditeur.
- Première ligne dans l'éditeur pour le message du commit
- Laisser une ligne vide
- Troisième ligne pour commenter le commit. Enregistrer et fermer.

Pour configurer l'éditeur text qu'on veut utiliser avec git pour les messages de commit par exemple : `git config --global core.editor [nom éditeur]`


## Exemple d'application :
```
// Sous réserve que l'on se situe sur la branch dev

git branch [mon nom]/[ma feature1]
git checkout [mon nom]/[ma feature1]
  // Ces deux précédente ligne peuvent être combinées en une seule : git checkout -b [mon nom]/[ma feature1]
  // L'option -b permet de créer la branch tout en s'y déplaçant avec checkout
// Codage
git add .
  // Suivi de tous (.) les fichiers modifiés
    // OU git add --all pour accepter la suppression de fichiers.
git commit -m "[message explicatif des interventions]
  // Faire des commits régulièrement
git push origin [mon nom]/[ma feature1]
  // Envoi de la branch perso sur le serveur distant
    // L'ajout de -u à push permet d'enregistrer la commande pour n'écrire plus que git push
    // Commande pratique surtout sur la branch master ou dev.
git checkout dev
git pull
  // Sans 'origin dev' : sous réserve qu'un 'pull -u' ait été fait avant
git checkout [mon nom]/[ma feature1]
git rebase dev
// OU git merge dev
  // Résolution de conflit à ce moment.
  // Si conflit :
    // git add --all
    // git commit -m 'fixed conflict in name_fichier.truc'
git checkout dev
git pull
  // Pour être sûr qu'il n'y a pas de changement pendant le temps de la résolution de conflit)
    // Retourner sur [mon nom]/[ma feature1] si changement et refaire les 3 commandes précédentes
// Aller sur github et créer la Pull Request
    
// Ce guide est à titre démonstratif et peut évoluer suivant le cas rencontré.
// Ne pas hésiter à se rapprocher de quelqu'un d'autre en cas de soucis avec les commandes !
```

## Text Editor

Il est important de configurer son éditeur de texte pour que l'indentation soit la même pour tous les membres du groupe car cela peut une une source continuelle de conflits et prises de tête. La configuration se fait en bas à droite dans l'éditeur de texte. Il est important d'utiliser des espaces car les tabulations peuvent avoir une taille fluctuante selon les éditeurs. Il faut ensuite définir un nombre d'espace à chaque tab. J'ai tendance à préférer 2 pour un code plus compact et facile à lire. L'important reste que tous les membres du projet adoptent la même convention.

Pour limiter les conflits il est important d'installer un plugin pour supprimer les whitespaces (espaces) inutiles et ajouter une ligne vide à la fin de chaque fichier (c'est bonne pratique et github le signale si ce n'est pas fait).

Pour *sublime* [ce plugin](https://packagecontrol.io/packages/Whitespace) semble très bien.

Pour *brackets* j'utilise "Show Whitespace VS" qui montre de façon agréable les whitespaces et "White Space Sanitizer" qui fait le ménage.

## Ressources

(pour l'instant niveau resources je ratisse assez large parce qu'on sait pas encore précisement ce qu'on va devoir faire)

##### Git

[Workflow git](https://github.com/Balatzar/guides/tree/master/protocol/git)

[Merge vs Rebase](https://www.atlassian.com/git/tutorials/merging-vs-rebasing/summary)
