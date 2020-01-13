[**&larr; retour à la Stack**](2Stack.md) &nbsp;&nbsp; | &nbsp;&nbsp; [**Tests** &rarr;](4Tests.md)

# Notre git flow

## Introduction
Les objectifs de ce flux de travail:
 - Pouvoir travailler à 7
 - Identifiers des objectifs grâce aux releases prévues 
 - Centraliser la gestion des revues et la qualité du code
 - Assurer une intégration continue
 - Eviter des bugs

# Table of contents
0. [Mise en place des remotes](#remotes)
1. [Branches](#branches)
2. [Environments](#environments)
3. [Faire un ticket](#tickets)
4. [Pull Requests](#pull-requests)

## Branches

Ces branches son des branches de références sur lesquelles nous **ne travaillons pas**.
On merge seulement dessus des Pull requests correspondant à une branche de ticket.

- `master` - always **stable** and **release ready** branch; (production)
- `develop` - default branch, contains latest **features** and **fixes**, on which developers should orient;
- `<nom-espace>_features/<nom-feature>` - branches feature development and dependencies update;
On utise des prefixes pour identifier un espace concerné.

## Remotes

**!! Avant tout !!** il faut bien vérifier qu'on a les bonnes remotes `origin` et `g4-dev`

#### entrez cette commande pour ajouter le repository parent à votre fork et mettre à jour vos branches

```
git remote add g4-dev git@github.com:g4-dev/src-ecs.git
```

On a donc deux repository ou remotes distantes :
- `origin` : notre fork là où l'on peut push
- `g4-dev` : notre repository parent où l'on fusionne le travail de chacun (**interdit de push**)

#### Trois espaces possibles :
  - **Core** (à ne pas trop toucher) &rarr; ***`core`***
  - **Portal** (FrontOffice) &rarr; ***`fo`***
  - **Admin** (BackOffice) &rarr; ***`bo`***

&rarr; exemple `bo_features/products`

- `release/version` - branches for release(production) version;
- `hotfix-*` - branches for release `fixes`;

#### Mettre à jour vos branches (IMPORTANT)

Avant de travailler sur un projet/ ou de merge une branche sur une des principales on se met à jour avec:

```
git fetch upstream
git rebase upstream <nom-de-la-branche-qui-a-la-maj>
```

Dans le cas d'une PR je dois push cette branche sur mon fork (origin) :

`git push -u origin <nom-branche>`

## Environments

On fonctionne avec deux interface principales :
- `github`
- `clickup`

Sur Clickup on récupère les tâches à faire et ensuite on les éxecute sur github.

Voici un exemple de workflow détaillé :

  1. Je **m'assigne** un ticket avec l'id `#34jeq3`

  ![image_ticket](res/start_ticket.png)

  2. Je créer une branche à partir de la dernière version de `develop` ou de la release proche
  ```
  git fetch upstream develop:#34jeq3
  git checkout #34jeq3
  ```

  3. Je code ma feature

  4. Je créer une PR

## Tickets

### Supporting readings

1. [Semantic Versioning 2.0.0](http://semver.org/)
2. [Git cheat sheet](https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf)
3. [Github help: user collaborating](https://help.github.com/categories/collaborating/)

