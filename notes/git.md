# GIT HELP
<!-- TOC START min:2 max:3 link:true asterisk:false update:true -->
- [Intro](#intro)
- [Moving around in Git](#moving-around-in-git)
- [Revirtiendo cambios](#revirtiendo-cambios)
- [Moviendo trabajo por ahí](#moviendo-trabajo-por-ahí)
- [Git Interactive Rebase](#git-interactive-rebase)
<!-- TOC END -->
## Intro
* https://learngitbranching.js.org/

**Commits**
>git commit  

**Ramas**
* Create branch
>git branch newImage
* Commit on branch
>git ckeckout newImage   
git commit  
* Branch: create and checkout
> git checkout -b [yourbranchname]

**Mergeando ramas**
* Option 1
>git merge bugFix  
![](https://antoniodiaz.github.io/images/git/git_merge_01.jpg)
* Option 2
>git checkout bugFix   
git merge master  
![](https://antoniodiaz.github.io/images/git/git_merge_02.jpg)
**Rebase**
* The second way of combining work between branches is rebasing. Rebasing essentially takes a set of commits, "copies" them, and plops them down somewhere else.
* While this sounds confusing, the advantage of rebasing is that it can be used to make a nice linear sequence of commits. The commit log / history of the repository will be a lot cleaner if only rebasing is allowed.  

>git rebase master  
![](https://antoniodiaz.github.io/images/git/git_rebase_01.jpg)  

>git rebase bugFix  
![](https://antoniodiaz.github.io/images/git/git_rebase_02.jpg)  

## Moving around in Git
**HEAD**
* it's essentially what commit you're working on top of.
* Normally HEAD points to a branch name (like bugFix). When you commit, the status of bugFix is altered and this change is visible through HEAD.
* Deteaching HEAD:
>git checkout C1  
![](https://antoniodiaz.github.io/images/git/git_head_01.jpg)

**Relative Refs**
* Moving upwards one commit at a time with ^
* Moving upwards a number of times with ~num  
>git checkout master^  

![](https://antoniodiaz.github.io/images/git/git_head_02.jpg)

>git checkout C3  
git checkout HEAD^  
git checkout HEAD^  
git checkout HEAD^  

![](https://antoniodiaz.github.io/images/git/git_head_03.jpg)

>git checkout HEAD~4  

![](https://antoniodiaz.github.io/images/git/git_head_04.jpg)

* Move branch:
>git branch -f master HEAD~3  

![](https://antoniodiaz.github.io/images/git/git_head_05.jpg)

## Revirtiendo cambios
* **Git Reset**: revierte los cambios moviendo la referencia de una rama hacia atras en el tiempo a un commit anterior.
Se puede ver como "reescribir la historia". git reset va a mover la rama hacia atrás, como si el commit nunca se hubiera hecho.
>git reset HEAD~4

![](https://antoniodiaz.github.io/images/git/git_reset_01.jpg)

* **Git Revert**: Mientras que resetear los cambios funciona genial para ramas locales en tu maquina,
su metodo de "reescribir la historia" no funciona para ramas remotas que otros estan usando.
Para revertir cambios y compartir esa revertida con otros, necesitamos usar git revert.
Cuando usas revert, puedes pushear ese cambio para compartirlo con otros.
Revert crea un nuevo commit aplicado sobre el que queriamos revertir.
>git revert HEAD

![](https://antoniodiaz.github.io/images/git/git_revert_01.jpg)


## Moviendo trabajo por ahí
* Git Cherry-pick: git cherry-pick Commit1 Commit2 ...
> git cherry-pick C2 C4

![](https://antoniodiaz.github.io/images/git/git_cherry_pick_01.jpg)

## Git Interactive Rebase
