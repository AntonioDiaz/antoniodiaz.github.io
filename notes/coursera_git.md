# Coursera: Version Control with Git

<!-- TOC depthfrom:2 updateonsave:true -->

- [Week 1](#week-1)
- [Week 2](#week-2)
- [Week 3](#week-3)
- [Week 4](#week-4)
- [CheatSheet](#cheatsheet)
    - [Git references](#git-references)
    - [Tags](#tags)
    - [Branches](#branches)
    - [Merging](#merging)
    - [Revolving conflicts](#revolving-conflicts)
    - [Tracking remote branches](#tracking-remote-branches)
    - [Network commands: clone, fetch, pull & push](#network-commands-clone-fetch-pull--push)
    - [Rebasing](#rebasing)
    - [Rewriting history](#rewriting-history)

<!-- /TOC -->



https://www.coursera.org/learn/version-control-with-git

## Week 1  
| | | |
|-|-|-|
| **Instalation and getting started**  |  [sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/01_01_installation_sourcetree.pdf)| [cli](https://antoniodiaz.github.io/notes/coursera/pdf/01_01_installation_cli.pdf) |
|**Create a git repository**|[sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/01_02_create_local_sourcetree.pdf)|[cli](https://antoniodiaz.github.io/notes/coursera/pdf/01_02_create_local_cli.pdf)
|**Commit to Local Repository**|[sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/01_03_commit_local_sourcetree.pdf)|[cli](https://antoniodiaz.github.io/notes/coursera/pdf/01_03_commit_local_cli.pdf)
|**Create a Remote Repository**|[sourcetree & cli](https://antoniodiaz.github.io/notes/coursera/pdf/01_04_create_remote.pdf)| |
|**Push to a Remote Repository**|[sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/01_05_push_sourcetree.pdf)|[cli](https://antoniodiaz.github.io/notes/coursera/pdf/01_05_push_cli.pdf)

## Week 2  
| | | |
|-|-|-|
|**Git References**  |[sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/02_01_references_sourcetree.pdf)  |[cli](https://antoniodiaz.github.io/notes/coursera/pdf/02_01_references_cli.pdf)
|**Branches**  | [sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/02_02_branches_sourcetree.pdf)  | [cli](https://antoniodiaz.github.io/notes/coursera/pdf/02_02_branches_cli.pdf)
|**Merging**  | [sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/02_03_merging_sourcetree.pdf)  | [cli](https://antoniodiaz.github.io/notes/coursera/pdf/02_03_merging_cli.pdf)

## Week 3  
| | | |
|-|-|-|
|**Resolving Merge Conflicts**  | [sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/03_01_conflicts_sourcetree.pdf)|[cli](https://antoniodiaz.github.io/notes/coursera/pdf/03_01_conflicts_cli.pdf)
|**Tracking Branches**  |[sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/03_02_trackingh_branches_sourcetree.pdf)  |[cli](https://antoniodiaz.github.io/notes/coursera/pdf/03_02_trackingh_branches_cli.pdf)
|**Fetch, Pull and Push**  | [sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/03_03_fetch_pull_push_sourcetree.pdf)  |[cli](https://antoniodiaz.github.io/notes/coursera/pdf/03_03_fetch_pull_push_cli.pdf)
|**Rebasing**  | [sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/03_04_rebasing_sourcetree.pdf)  | [cli](https://antoniodiaz.github.io/notes/coursera/pdf/03_04_rebasing_cli.pdf)
|**Rewriting History**  |[sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/03_05_rewriting_sourcetree.pdf)  | [cli](https://antoniodiaz.github.io/notes/coursera/pdf/03_05_rewriting_cli.pdf)

## Week 4  
| | | |
|-|-|-|
|**Pull Request I**  |[sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/04_01_pull_request_1_sourcetree.pdf)  | [cli](https://antoniodiaz.github.io/notes/coursera/pdf/04_01_pull_request_1_cli.pdf)
|**Pull Request II**  | [sourcetree](https://antoniodiaz.github.io/notes/coursera/pdf/04_02_pull_request_2_sourcetree.pdf)  | [cli](https://antoniodiaz.github.io/notes/coursera/pdf/04_02_pull_request_2_cli.pdf)

## CheatSheet
### Git references
``` bash
git log --oneline --graph -1
git show 483d
git show head
git show tag_name
git show master~~ --> parent parent
git show master^2 --> second parent num
git status
```

### Tags
``` bash
git tag --> show all tags in the repository
git show v0.1
git tag <tagname> [<commit>] --> create a lightweight tag
git tag -a [-m <message>] [ -F <file>] <tagname> [<commit>]
git push <remote> <tagname>
git push origin --tags
```

### Branches
``` bash
git branch --> to see list of branches
git branch -a --> to see local and remote branches
git branch <name> --> crate a branch
git checkout <branch_or_commit>  --> checkout branch
git checkout -b <branch> --> create and checkout the branch
```

* delete branch
``` bash
git branch -d <branch> --> delete branch label
git branch -D <branch> --> delete branch with commits not merged
```
* undoing an accidental branch delete
``` bash
git reflogs --> returns a local list
git checkout -b <branch> <sha1>
```

### Merging
* fast-forward merge, just change the label, only possible if in original branch has not commit after the branch.
``` bash
git checkout master
git merge featureX      //fast-forward default option
git branch -d featureX
```

* merge commit (no fast-forward)
``` bash
git checkout master
git merge --no-ff featureX
git branch -d featureX
```
### Revolving conflicts
``` bash
git merge featureX --> conflic
git merge --abort
git add <file> --> after resolving conflict
git commit 
```


### Tracking (remote) branches
``` bash
git branch --all
--default remote tracking branch
git log origin/master --oneline
git log origin --oneline
git remote set-head <remote> <branch> --> change default remote tracking branch.
git remote set-head origin develop
git log --all
```

### Network commands: clone, fetch, pull & push
* CLONE: copies a remote repository
* FETCH: retrieves new objects and references from the remote repository
``` bash
git fetch <repository>
```
* PULL: fetches and merges commits locally
pull merging options
--ff
--no-ff
--ff-only
--rebase [--preserve-merge]


* PUSH: adds new objects and references to the remote repository
```bash
git push [-u] [<repository>] [<branch>]
```

### Rebasing
<img src="https://antoniodiaz.github.io/images/git_coursera/merge_and_rebase.png" width="600"/>  
  
```bash
//option 1
git rebase <upstream>
git checkout featureX
git rebase master
//option 2
git rebase <upstream> <branch>
git rebase master featureX

git rebase --continue
```

### Rewriting history
* Amending a commit: change the most recent commit (message or files)
``` bash
//update last commit message
git commit --amend -m "correct message"
//update files but keep commit message
git commit --amend --no-edit
```
* Interactive rebase (do not use for shared commits)
<img src="https://antoniodiaz.github.io/images/git_coursera/interactive_rebase.png" width="600"/>  
``` bash
git rebase -i <after-this-commit>
```


