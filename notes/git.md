# GIT HELP
<!-- TOC START min:2 max:4 link:true asterisk:false update:true -->
- [Intro](#intro)
    - [Commit](#commit)
    - [Merge](#merge)
- [Moving around in Git](#moving-around-in-git)
- [Reversing Changes](#reversing-changes)
- [Moviendo trabajo por ahí](#moviendo-trabajo-por-ahí)
- [Git Interactive Rebase](#git-interactive-rebase)
<!-- TOC END -->
## Intro
* https://learngitbranching.js.org/

### Commit
>git commit  

**Branches and Merging**
* Create branch:
> git branch newImage
* Commit on branch
> git ckeckout newImage  
git commit  
* Branch: create and checkout
> git checkout -b [yourbranchname]

### Merge
* Step 1
>git merge bugFix  
<img src="https://antoniodiaz.github.io/images/git/git_merge_01.jpg" width="400"/>  

* Step 2
>git checkout bugFix   
git merge master  
<img src="https://antoniodiaz.github.io/images/git/git_merge_02.jpg" width="400"/>

**Rebase**
* The second way of combining work between branches is rebasing. Rebasing essentially takes a set of commits, "copies" them, and plops them down somewhere else.
* While this sounds confusing, the advantage of rebasing is that it can be used to make a nice linear sequence of commits. The commit log / history of the repository will be a lot cleaner if only rebasing is allowed.  

>git rebase master  
<img src="https://antoniodiaz.github.io/images/git/git_rebase_01.jpg" width="400"/>  

>git rebase bugFix  
<img src="https://antoniodiaz.github.io/images/git/git_rebase_02.jpg" width="400"/>  

## Moving around in Git
**HEAD**
* First we have to talk about "HEAD". HEAD is the symbolic name for the currently checked out commit -- it's essentially what commit you're working on top of.

* HEAD always points to the most recent commit which is reflected in the working tree. Most git commands which make changes to the working tree will start by changing HEAD.

* Normally HEAD points to a branch name (like bugFix). When you commit, the status of bugFix is altered and this change is visible through HEAD.

* Deteaching HEAD:
>git checkout C1  
<img src="https://antoniodiaz.github.io/images/git/git_head_01.jpg" width="400"/>  

**Relative Refs**
* Moving upwards one commit at a time with ^
>git checkout master^  
<img src="https://antoniodiaz.github.io/images/git/git_head_02.jpg"   width="400"/>  
>git checkout C3  
git checkout HEAD^  
git checkout HEAD^  
git checkout HEAD^  
<img src="https://antoniodiaz.github.io/images/git/git_head_03.jpg" width="400"/>  
* Moving upwards a number of times with ~num  
>git checkout HEAD~4  
<img src="https://antoniodiaz.github.io/images/git/git_head_04.jpg" width="400"/>  

**Move branch**
* One of the most common ways I use relative refs is to move branches around. You can directly reassign a branch to a commit with the -f option.  
>git branch -f master HEAD~3  
<img src="https://antoniodiaz.github.io/images/git/git_head_05.jpg" width="400"/>  

## Reversing Changes
* There are many ways to reverse changes in Git. And just like committing, reversing changes in Git has both a low-level component (staging individual files or chunks) and a high-level component (how the changes are actually reversed).  

**Git Reset**  
* *git reset* reverts changes by moving a branch reference backwards in time to an older commit. In this sense you can think of it as "rewriting history;" git reset will move a branch backwards as if the commit had never been made in the first place.  

>git reset HEAD~4  
<img src="https://antoniodiaz.github.io/images/git/git_reset_01.jpg" width="400"/>  

**Git Revert**
* While resetting works great for local branches on your own machine, its method of "rewriting history" doesn't work for remote branches that others are using.
* In order to reverse changes and share those reversed changes with others, we need to use git revert. Let's see it in action.  

>git revert HEAD  
<img src="https://antoniodiaz.github.io/images/git/git_revert_01.jpg" width="400"/>  


## Moviendo trabajo por ahí
* Git Cherry-pick: git cherry-pick Commit1 Commit2 ...
> git cherry-pick C2 C4

![](https://antoniodiaz.github.io/images/git/git_cherry_pick_01.jpg)

## Git Interactive Rebase
