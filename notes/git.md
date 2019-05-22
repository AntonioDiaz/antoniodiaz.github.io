# GIT HELP
https://learngitbranching.js.org/
## Intro 
* Commits de Git
>git commit
## Ramas git
  * Create branch
  >git branch newImage
  * Commit on branch
  >git ckeckout newImage; git commit

## Mergeando ramas
* Option 1
>git merge bugFix
* Option 2
>git checkout bugFix; git merge master

## Git Rebase
* Rebasear escencialmente agarra un conjunto de commits, los "copia", y los aplica sobre algún otro lado.
* Aunque esto pueda sonar confuso, la ventaja de rebasear es que puede usarse para conseguir una secuencia de commits lineal, más bonita. El historial / log de commits del repositorio va a estar mucho más claro si sólo usás rebase.
>git rebase master  
![](https://antoniodiaz.github.io/images/git/git_rebase.jpg)  
>git rebase bugFix  
![](https://antoniodiaz.github.io/images/git/git_rebase_02.jpg)  




detached: 
>git checkout C1
move to another branch: 
>git checkout fixBug
Referencias relativas:
* Mueve el HEAD al padre del master
>git checkout master^

## Revirtiendo cambios
* **Git Reset**: revierte los cambios moviendo la referencia de una rama hacia atrás en el tiempo a un commit anterior. En este sentido podés pensarlo como "reescribir la historia". git reset va a mover la rama hacia atrás, como si el commit nunca se hubiera hecho.
>git reset HEAD~4

* **Git Revert**: Mientras que resetear los cambios funciona genial para ramas locales en tu máquina, su método de "reescribir la historia" no funciona para ramas remotas que otros están usando.
Para revertir cambios y compartir esa revertida con otros, necesitamos usar git revert. Veámoslo en acción
Cuando usás revert, podés pushear ese cambio para compartirlo con otros.
Revert crea un nuevo commit aplicado sobre el que queríamos revertir.
>git revert HEAD

## Moviendo trabajo por ahí
* Git Cherry-pick
>git cherry-pick <Commit1> <Commit2> <...>
