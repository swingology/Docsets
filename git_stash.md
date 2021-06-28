# Git Stash

git stash is a 'clipboard' for changes to a branch that we don't want to commit
@todo set vim diff as git diff

## quick start
1. git stash [push] -> stores whatever changes you made into a stash
2. do what you have to do
3. git stash pop -> restores whatever you stashed

## git stash commands

| Command                | Action                                                                                                | Options                                       |
| ---------------------- | ----------------------------------------------------------------------------------------------------- | --------------------------------------------- |
|                        | creates a quick snapshot                                                                              |                                               |
| push                   | save local modifications onto a new stash entry                                                       | -p -k -u -a -q -m --pathspec-from-file=<file> |
| list                   | list all current stashes (stash@{#})                                                                  | <log-options>                                 |
| show <stash>           | show the diff between stash changes and current working tree state                                    | -u <diff-options>                             |
| pop <stash>            | apply a stashed state on top of the current working tree state and remove it from the list of stashes | --index -q                                    |
| apply <stash>          | like pop but does not remove the stash entry                                                          | --index -q                                    |
| branch <branch><stash> | creates and checks out a new branch with the changes from stash                                       |                                               |
| clear                  | remove all stash entries                                                                              |                                               |
| drop                   | remove a single stash entry                                                                           | -q                                            |
| create                 | create a stash entry (for scripts)                                                                    |                                               |
| store                  | store a given stash (for scripts)                                                                     |                                               |

## git stash options

| Option                                                                       | Action                                                                          |
| ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| <stash>                                                                      | reference of the form of stash@{<revision>}                                     |
| -a \| --all                                                                  | all ignored and untracked files are stashed                                     |
| -u \| --include-untracked \| <br/>--no-include-untracked \| --only untracked | push or show all \| no untracked files \| show only untracked files             |
| --index                                                                      | tries to reinstate not only the working tree changes, but also the index's ones |
| -k \| --keep-index \| --no-keep-index                                        | all changes already added to the index are left intact                          |
| -p \| --patch                                                                | interactively diff between head and the working tree to be stashed              |
| -q \| --quiet                                                                | quiet/suppress feedback messages                                                |

