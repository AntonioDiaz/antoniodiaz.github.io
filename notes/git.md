# GIT HELP
<!-- TOC START min:2 max:4 link:true asterisk:false update:true -->
- [Intro](#intro)
    - [Commit](#commit)
    - [Merge](#merge)
- [Moving around in Git](#moving-around-in-git)
- [Reversing Changes](#reversing-changes)
- [Moving Work Around](#moving-work-around)
    - [Cherry-pick](#cherry-pick)
    - [Git Interactive Rebase](#git-interactive-rebase)
- [A Mixed Bag](#a-mixed-bag)
    - [Grabbing Just 1 Commit](#grabbing-just-1-commit)
    - [Juggling Commits 1](#juggling-commits-1)
    - [Juggling Commits 2](#juggling-commits-2)
    - [Git Tags](#git-tags)
    - [Git Describe](#git-describe)
- [Advanced Topics](#advanced-topics)
    - [Rebasing over 9000 times](#rebasing-over-9000-times)
    - [Multiple parents](#multiple-parents)
    - [Branch Spaghetti](#branch-spaghetti)
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


## Moving Work Around
### Cherry-pick
* Syntax: *git cherry-pick Commit1 Commit2 ...*
* It's a very straightforward way of saying that you would like to copy a series of commits below your current location (HEAD). I personally love cherry-pick because there is very little magic involved and it's easy to understand.  

> git cherry-pick C2 C4  
<img src="https://antoniodiaz.github.io/images/git/git_cherry_pick_01.jpg" width="400"/>  

### Git Interactive Rebase
* Cherry-pick is great when you know which commits you want (and you know their corresponding hashes), it's hard to beat the simplicity it provides.
* But what about the situation where you don't know what commits you want? Thankfully git has you covered there as well! We can use interactive rebasing for this, it's the best way to review a series of commits you're about to rebase.
* All interactive rebase means is using the rebase command with the -i option.
* If you include this option, git will open up a UI to show you which commits are about to be copied below the target of the rebase. It also shows their commit hashes and messages, which is great for getting a bearing on what's what.
* For "real" git, the UI window means opening up a file in a text editor like vim. For our purposes, I've built a small dialog window that behaves the same way.
* When the **interactive rebase dialog** opens, you have the ability to do 3 things:
  * You can **reorder commits** simply by changing their order in the UI (in our window this means dragging and dropping with the mouse).
  * You can choose to completely **omit some commits**. This is designated by pick, toggling pick off means you want to drop the commit.
  * Lastly, you can **squash commits**. Unfortunately our levels don't support this for a few logistical reasons, so I'll skip over the details of this. Long story short, though -- it allows you to combine commits.  

>git rebase -i HEAD~4  
<img src="https://antoniodiaz.github.io/images/git/git_interactive_rebase_01.jpg" width="400"/>

## A Mixed Bag
### Grabbing Just 1 Commit
### Juggling Commits 1
### Juggling Commits 2
### Git Tags
### Git Describe

## Advanced Topics
### Rebasing over 9000 times
### Multiple parents
### Branch Spaghetti
