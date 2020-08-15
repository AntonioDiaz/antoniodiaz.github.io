# Coursera: Version Control with Git

<!-- TOC depthfrom:2 updateonsave:true -->

- [Week 1](#week-1)
- [Week 2](#week-2)
- [Week 3](#week-3)
- [Week 4](#week-4)
- [CheatSheet](#cheatsheet)

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
* Git references
```shell
git log --oneline --graph -1
git show 483d
git show head
git show tag_name
git show master~~ --> parent parent
git show master^2 --> second parent num
git status
```

* Tags
```shell
git tag --> show all tags in the repository
git show v0.1
git tag <tagname> [<commit>] --> create a lightweight tag
git tag -a [-m <message>] [ -F <file>] <tagname> [<commit>]
git push <remote> <tagname>
git push origin --tags
```

* Branches
```shell
git branch -a
//create branch
git branch <name>
//checkout branch
//delete branch label
git branch -d <name>
```