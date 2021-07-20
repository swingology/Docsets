# GIT/GITHUB CHEATSHEET


| SHORTCUT                       | ACTIONS                                                       |
|--------------------------------|---------------------------------------------------------------|
| BRANCHES                       |                                                               |
| git checkout -b <NewBranch>    | Create a <NewBranch>                                          |
| git branch -d <branchName>     | Delete Branch                                                 |
|                                |                                                               |
| MERGING                        |                                                               |
| git checkout master            | swithing to revert tot he previous commit on master           |
| git revert -m 1 <commit-hash>  | revert to branch merged into (2 for revert to merging branch) |
|                                |                                                               |
| git reflog                     | checks log to see when refs were updated                      |
| git reset --hard <commit-hash> | RESETTING before a push                                       |
| git reset --hard HEAD~1        |                                                               |
| git reset --hard ORIG_HEAD     |                                                               |
| git reset --merge ORIG_HEAD    |                                                               |
| git merge --abort              | Modern git                                                    |
| git reset --merge              |                                                               |
| git reset --hard               |                                                               |
| git merge --abort              |                                                               |
|                                |                                                               |
| git pull <main>                | while in another branch merges branches                       |
|                                |                                                               |
|                                |                                                               |
| git reset <file>               | undo git add <file>                                           |
| git reset                      | undo git add .                                                |
|                                |                                                               |
|                                |                                                               |
| git reset 'HEAD@{1}            | undo a git RESET   - look up why {1}                          |
| git reset -soft Head~x         |                                                               |
| git reset -soft <commit_hash>  | undo recent git COMMITS                                       |
|                                |                                                               |
| git reset — hard HEAD@{5}      | Undo a rebase at hold commit HEAD5                            |
|                                |                                                               |






## LINKS
| @reflog: | https://www.atlassian.com/git/tutorials/rewriting-history/git-reflog |
| @undo:    | https://betterprogramming.pub/undoing-in-git-39e4404c0e92 |



