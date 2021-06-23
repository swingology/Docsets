



## DOCUMENTATION
- [ ] git commit-tree 
- [ ] git log
	- git log --oneline --graph --decorate --merges
	-
- [ ] git status
- [ ] git diff
- [ ] git config
- [ ] git hooks
- [ ] git merge
- [ ] using sha's to look at info
- [ ] gh_cli gist management
-
	### SECONDARY
	git whatchanged
	git bisect 
	git cherry
	tags in git
## Links

[Git - git-branch Documentation](https://git-scm.com/docs/git-branch)

https://gist.github.com/m14t/3056747



## github branch
git branch [--color[=<when>] | --no-color] [--show-current]
    [-v [--abbrev=<n> | --no-abbrev]]
    [--column[=<options>] | --no-column] [--sort=<key>]
    [--merged [<commit>]] [--no-merged [<commit>]]
    [--contains [<commit>]] [--no-contains [<commit>]]
    [--points-at <object>] [--format=<format>]
    [(-r | --remotes) | (-a | --all)]
    [--list] [<pattern>…​]
git branch [--track | --no-track] [-f] <branchname> [<start-point>]
git branch (--set-upstream-to=<upstream> | -u <upstream>) [<branchname>]
git branch --unset-upstream [<branchname>]
git branch (-m | -M) [<oldbranch>] <newbranch>
git branch (-c | -C) [<oldbranch>] <newbranch>
git branch (-d | -D) [-r] <branchname>…​
git branch --edit-description [<branchname>



## SSH AGENT MULTIPLE ACCOUNT LOGIN TO GITHUB
Multiple github

 [GitHub CLI and how to get started](https://devdojo.com/bobbyiliev/what-is-github-cli-and-how-to-get-started)

```
gh auth login
```

-----

[Working with SSH key passphrases - GitHub Docs](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/working-with-ssh-key-passphrases)

[Ssh-add program usage with ssh-agent and SSH keys. How to enable SSH public key authentication and single sign-on.](https://www.ssh.com/academy/ssh/add)

ssh-agent

eval $('ssh-agent')

ssh-add ~/,.ssh/<rsa__key>

[How to manage multiple GitHub accounts on a single machine with SSH keys](https://www.freecodecamp.org/news/manage-multiple-github-accounts-the-ssh-way-2dadc30ccaca/)

### SSH-AGENT

@GithubCLI @cheatsheet

To create a repository non-interactively, supply the following:

- the name argument;
- the `--confirm` flag;
- one of `--public`, `--private`, or `--internal`.

To toggle off `--enable-issues` or `--enable-wiki`, which are enabled
by default, use the `--enable-issues=false` syntax.






######################



# notesi
$ tree .git/refs
.git/refs
├── heads
│   └── master
├── hg
│   └── origin
│       ├── bookmarks
│       │   └── master
│       └── branches
│           └── default
├── notes
│   └── hg
├── remotes
│   └── origin
│       └── HEAD
└── tags

git ls -tree sha
