# GIT LOG REFERENCE
@snippets: @git: @ref:
[Git Log Reference](https://git-scm.com/docs/git-log)
ONLY A FEW OPTIONS LISTED

``` bash

git log <options> <revision range> [--] <path>




```

**Shows Commit Log**



``` bash

# EXAMPLES
git log foo bar ^baz            - list all commits reachjabel from foo or bar NOT baz

git log origin..HEAD
git log HEAD ^origin            - means same as above


git log A B --not $(git merge-base --all A B)
git log A..B

git log --pretty=oneline

```

https://www.atlassian.com/git/tutorials/saving-changes/git-diff

``` bash
git diff --color-words
git diff-highlight
git diff HEAD ./path/to/file
git diff --cached ./path/to/file


# shows the difference for last commit
git diff <commit id>
git diff <commit1> <commit2>


# comparing different branches
git diff <branch1>..<branch2>
git diff branch1..other-feature-branch





#comparing files from different branches
git diff <branc1> <branch2> <file>
git diff main new_branch ./diff-test.txt



# can run diff of binary files
git diff 
>>> Binary files a/script.pdf and b/script.pdf differ

```



## READING GIT DIFF RESULTS
``` bash
1> diff --git a/vim_plugins_cheatsheet.md b/vim_plugins_cheatsheet.md
2> index a538c67..fe1dde5 100644
3> --- a/vim_plugins_cheatsheet.md
4> +++ b/vim_plugins_cheatsheet.md
5> @@ -1,35 +1,119 @@
```


1. comparison input
2. meta data
3. markers for changes
4. markers for changes
5. diff chunk
    > @@ -1,35 +1,119@@
    > @@ are encloseing symbols
    > -1,35         - 35 line extracted starting from line 1
    > +1,119        - 119 lines have been added since line 1
    
    




## NOTE ON COMPARING PDFS
Git does have a feature that allows you to specify a shell command to transform the content of your binary files into text prior to performing the diff. It does require a little set up though. First, you need to specify a textconv filter describing how to convert a certain type of binary to text. We're using a simple utility called pdftohtml (available via homebrew) to convert my PDFs into human readable HTML. You can set this up for a single repository by editing your .git/config file, or globally by editing ~ /.gitconfig

``` bash

# in the .gitcongi
[diff "pdfconv"]
textconv=pdftohtml -stdout
```

Then all you need to do is associate one or more file patterns with our pdfconv filter. You can do this by creating a .gitattributes file in the root of your repository.
``` bash
*.pdf diff=pdfconv

```







### OPTIONS
i
--all
--no-decorate [=short|full|auto|no]                     - Print out ref names of any commits
--source                                                - Print out ref name given on the command line
--full-diff
--log-size
-L<start>,<end>:<file>
-L:<functionname>:<file>                                - trace evolution of the line range or funciton name regex within file
<start> to <end>                                        - number or regex or offset
-cherry -mark
--cherry-pick                                           - omit any commit that introduces the smae change as another commit
--left-only
--right-only
--merge                                                 - after a fail merge show refs
<!---- DEFAULT OPTIONS --->
--show-pulls
--full-history
--dense
-sparse

<!---- COMMIT FORMATTING ----->
--pretty
--format=<format>
--abbrev-commmit
--no-abbrev-commit
--oneline
--encoding
--notes
--date
--parents
--children
--left-right
--graph


## MUST LOOK AT PLACE HOLDERS
## MUST LOOK AT DIFF FORMATTING
## HERE ARE HTE OPTIONS TO LOOK AT DIFF-MERGES
--color



