# GIT HELP
https://learngitbranching.js.org/
## Intro: 
* Commits de Git
>git commit
* Ramas git
>git branch newImage

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
