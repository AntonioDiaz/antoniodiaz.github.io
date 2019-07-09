 # GIT HELP
<!-- TOC START min:2 max:4 link:true asterisk:false update:true -->
- [Intro](#intro)
    - [Commit](#commit)
    - [Merge](#merge)
- [Moving around in Git](#moving-around-in-git)
    - [HEAD](#head)
    - [Relative Refs](#relative-refs)
    - [Move branch](#move-branch)
- [Reversing Changes](#reversing-changes)
    - [Git Reset](#git-reset)
    - [Git Revert](#git-revert)
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
### HEAD
* First we have to talk about "HEAD". HEAD is the symbolic name for the currently checked out commit -- it's essentially what commit you're working on top of.

* HEAD always points to the most recent commit which is reflected in the working tree. Most git commands which make changes to the working tree will start by changing HEAD.

* Normally HEAD points to a branch name (like bugFix). When you commit, the status of bugFix is altered and this change is visible through HEAD.

* Deteaching HEAD:
>git checkout C1  
<img src="https://antoniodiaz.github.io/images/git/git_head_01.jpg" width="400"/>  

### Relative Refs
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

### Move branch
* One of the most common ways I use relative refs is to move branches around. You can directly reassign a branch to a commit with the -f option.  
>git branch -f master HEAD~3  
<img src="https://antoniodiaz.github.io/images/git/git_head_05.jpg" width="400"/>  

## Reversing Changes
* There are many ways to reverse changes in Git. And just like committing, reversing changes in Git has both a low-level component (staging individual files or chunks) and a high-level component (how the changes are actually reversed).  

### Git Reset
* *git reset* reverts changes by moving a branch reference backwards in time to an older commit. In this sense you can think of it as "rewriting history;" git reset will move a branch backwards as if the commit had never been made in the first place.  

>git reset HEAD~4  
<img src="https://antoniodiaz.github.io/images/git/git_reset_01.jpg" width="400"/>  

### Git Revert
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
* Here's a development situation that often happens: I'm trying to track down a bug but it is quite elusive. In order to aid in my detective work, I put in a few debug commands and a few print statements.
* All of these debugging / print statements are in their own commits. Finally I track down the bug, fix it, and rejoice!
* Only problem is that I now need to get my bugFix back into the master branch. If I simply fast-forwarded master, then master would get all my debug statements which is undesirable. There has to be another way...
* We need to tell git to copy only one of the commits over. This is just like the levels earlier on moving work around -- we can use the same commands:
  * *git rebase -i*
  * *git cherry-pick*

### Juggling Commits 1
* Here's another situation that happens quite commonly. You have some changes (newImage) and another set of changes (caption) that are related, so they are stacked on top of each other in your repository (aka one after another).
* The tricky thing is that sometimes you need to make a small modification to an earlier commit. In this case, design wants us to change the dimensions of newImage slightly, even though that commit is way back in our history!!
* We will overcome this difficulty by doing the following:
  * We will re-order the commits so the one we want to change is on top with git **rebase -i**
  * We will **commit --amend** to make the slight modification
  * Then we will re-order the commits back to how they were previously with **git rebase -i**
  * Finally, we will move master to this updated part of the tree to finish the level (via the method of your choosing).
* There are many ways to accomplish this overall goal (I see you eye-ing cherry-pick), and we will see more of them later, but for now let's focus on this technique. Lastly, pay attention to the goal state here -- since we move the commits twice, they both get an apostrophe appended. One more apostrophe is added for the commit we amend, which gives us the final form of the tree.
* That being said, I can compare levels now based on structure and relative apostrophe differences. As long as your tree's master branch has the same structure and relative apostrophe differences, I'll give full credit.

### Juggling Commits 2
* As you saw in the last level, we used rebase -i to reorder the commits. Once the commit we wanted to change was on top, we could easily --amend it and re-order back to our preferred order.
* The only issue here is that there is a lot of reordering going on, which can introduce rebase conflicts. Let's look at another method with git cherry-pick.
* So in this level, let's accomplish the same objective of amending C2 once but avoid using rebase -i. I'll leave it up to you to figure it out! :D
* Remember, the exact number of apostrophe's (') on the commit are not important, only the relative differences. For example, I will give credit to a tree that matches the goal tree but has one extra apostrophe everywhere.

### Git Tags
* As you have learned from previous lessons, branches are easy to move around and often refer to different commits as work is completed on them. Branches are easily mutated, often temporary, and always changing.
* If that's the case, you may be wondering if there's a way to permanently mark historical points in your project's history. For things like major releases and big merges, is there any way to mark these commits with something more permanent than a branch?
* Git tags support this exact use case -- they (somewhat) permanently mark certain commits as "milestones" that you can then reference like a branch.
* More importantly though, they never move as more commits are created. You can't "check out" a tag and then complete work on that tag -- tags exist as anchors in the commit tree that designate certain spots.
> git tag V1 C1  
We named the tag v1 and referenced the commit C1 explicitly. If you leave the commit off, git will just use whatever HEAD is at.  
<img src="https://antoniodiaz.github.io/images/git/git_tag_01.jpg" width="200"/>

### Git Describe
* Because tags serve as such great "anchors" in the codebase, git has a command to describe where you are relative to the closest "anchor" (aka tag). And that command is called git describe!
* Git describe can help you get your bearings after you've moved many commits backwards or forwards in history; this can happen after you've completed a git bisect (a debugging search) or when sitting down at a coworkers computer who just got back from vacation.
* Git describe takes the form of:
> **git describe &lt;ref&gt;**  
Where &lt;ref&gt; is anything git can resolve into a commit. If you don't specify a ref, git just uses where you're checked out right now (HEAD).
* The output of the command looks like:
>**&lt;tag&gt;_&lt;numCommits&gt;_g&lt;hash&gt;**  
Where tag is the closest ancestor tag in history, numCommits is how many commits away that tag is, and <hash> is the hash of the commit being described.  
* Example
>git tag v2 C3  
<img src="https://antoniodiaz.github.io/images/git/git_describe_01.jpg" width="400"/>  
The command *git describe master* would output:  
v1_2_gC2  
Whereas *git describe side* would output:  
v2_1_gC4  

## Advanced Topics
### Rebasing over 9000 times
* Man, we have a lot of branches going on here! Let's rebase all the work from these branches onto master.
* Upper management is making this a bit trickier though -- they want the commits to all be in **sequential order**. So this means that our final tree should have C7' at the bottom, C6' above that, and so on, all in order.
* If you mess up along the way, feel free to use reset to start over again. Be sure to check out our solution and see if you can do it in fewer commands!
### Multiple parents
* Like the ~ modifier, the ^ modifier also accepts an optional number after it.
* Rather than specifying the number of generations to go back (what ~ takes), the modifier on ^ specifies which parent reference to follow from a merge commit. Remember that merge commits have multiple parents, so the path to choose is ambiguous.
* Git will normally follow the "first" parent upwards from a merge commit, but specifying a number with ^ changes this default behavior.

>git checkout master^  
Here we have a merge commit. If we checkout master^ without the modifier, we will follow the first parent after the merge commit.
(In our visuals, the first parent is positioned directly above the merge commit.)  
<img src="https://antoniodiaz.github.io/images/git/git_multiple_parents_01.jpg" width="400"/>  

>git checkout master^2  
<img src="https://antoniodiaz.github.io/images/git/git_multiple_parents_02.jpg" width="400"/>  

* The ^ and ~ modifiers can make moving around a commit tree very powerful:  

>git checkout HEAD~  
git checkout HEAD^2  
git checkout HEAD~2  
<img src="https://antoniodiaz.github.io/images/git/git_multiple_parents_03.jpg" width="400"/>  

* Even crazier, these modifiers can be chained together! Check this out:  

>git checkout HEAD~^2~2  
<img src="https://antoniodiaz.github.io/images/git/git_multiple_parents_03.jpg" width="400"/>  

### Branch Spaghetti
* Here we have master that is a few commits ahead of branches one two and three. For whatever reason, we need to update these three other branches with modified versions of the last few commits on master.
* Branch one needs a re-ordering and a deletion of C5. two needs pure reordering, and three only needs one commit!
* We will let you figure out how to solve this one -- make sure to check out our solution afterwards with show solution.
