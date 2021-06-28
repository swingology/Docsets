scratch buffers



## TODO
- [ ] man vimdiff
- [ ] :h vimdiff
- [ ] :h :diffthis
- [ ] :h :diffoff
- [ ] :h :windo
- [ ] :h :vnew
- [ ] :help 08.7
- [ ] :h :put
- [ ] :h quoteplus
- [ ] :h ctrl-w_s
- [ ] :h ctrl-w_v
- [ ] @fix: vim-arline tabline
- [ ] @m1mac: @markdown: @plugin: autocommplete charts


# LINKS
@vim: @oconfig:
https://www.reddit.com/r/neovim/comments/cfdxo9/do_i_need_set_t_co256/




@shortcut:
https://unix.stackexchange.com/questions/93144/exit-vim-more-quickly






## QUICK ACTIONS
### Vim Navigation  @VIM: @NAVI: 
"Max out the height of the current split
ctrl + w _

"Max out the width of the current split
ctrl + w |

"Normalize all split sizes, which is very handy when resizing terminal
ctrl + w =

More split manipulation

"Swap top/bottom or left/right split
Ctrl+W R

"Break out current window into a new tabview
Ctrl+W T

"Close every window in the current tabview but the current one
Ctrl+W o
()
{}

ctrl-w v                - open v split 
ctrl-w s                - open h splits
13gg  - go to line 13



### FROM BASH
vi +commandHere file
vi +LineNumber file
vi +/isearchTerm File

rg then use this shorcut


### FROM VIM




| <ESC> 42 shift-g  | goto line 42| nv | 
| :114              | go to line 114 |nv|




## VIM DIFF

### Vimdiff Links
https://www.cs.auckland.ac.nz/references/gnu/vim/diff.html
https://vi.stackexchange.com/questions/625/how-do-i-use-vim-as-a-diff-tool
[comparing buffers with vimdiff](http://vimcasts.org/episodes/comparing-buffers-with-vimdiff/)
https://gist.github.com/mattratleph/4026987
https://www.linux.com/news/vim-tips-moving-around-using-marks-and-jumps/
https://github.com/chrisbra/vim-diff-enhanced



### Starting vim diff from Console

``` bash
$ vimdiff <filea> <fileb>
$ vim -d <filea> <fileb>
$ vim -o <file> <file >  | open diff in vert split | 
```



### Starting from inisde diff

:vert diffsplit <filename>
:vs <other file>

#### Settings inside 




``` bash
:set scrollbind  or scb
:set noscrollbiind  or scb!
:set cursorbind
# other options
scrollopt
wrap 
foldmethod
foldcolumn

# setting default global difftool diff
@GIT: @CONFIG: @DIFF
git config --global diff.tool vimdiff

```
| :set wrap | wrap lines |
| :syn off | turn off color|



enter edit mode
:diffupdate



| ctrl-w ctrl-w | switch windows | nv |@diff: | @vim: | 
| **Navigating** |  | | | | 
| [c  | Prev difference |  | | | 
| ]c  | Next difference | | | | 


| **Editing** |  | | | | 
| :do | pull change from focused file | ||| 
| :dp | diff put - push the changes to other file | | | | 
| :diffget | change from otherwindow to current window | | | | 
| :diffput | put chnages from current window to other window | | | | 
| :diffupdate | can the files for differences | | | | 
| :diffoff | turn off diff mode ||||
| ZQ | quit without checking changes | 
| :windo diffthis | one step diff mode for window | 
| :windo diffoff | one step diff off for win |
| :only | this shows only the merged file | 

| **Folds** |  | | | |
| zo / zO | 	Open| | nv  | @diff: @folds: |@vim: |
| zc / zC | 	Close| | nv  | @diff: @folds: |@vim: |
| za / zA | 	Toggle| | nv  | @diff: @folds: |@vim: |
| zv 	    |     Open folds for this line| | nv  | @diff: @folds: |@vim: |
| zM 	    |     Close all| | nv  | @diff: @folds: |@vim: |
| zR 	    |     Open all| | nv  | @diff: @folds: |@vim: |
| zm 	    |     Fold more (foldlevel += 1)| | nv  | @diff: @folds: |@vim: |
| zr 	    |     Fold less (foldlevel -= 1)| | nv  | @diff: @folds: |@vim: |
| izx 	    |     Update folds| | nv  | @diff: @folds: |@vim: |



### VIM DIFF WORKFLOW
open 2 files in splits
[ vim open link] ()
[ itemrinal open link] ()       @FIXME:

:diffthis                       INCLUDFE FIRST FILE IN DIFF
:ctrl-w ctrl-w 
:diffthis                       INCLUDE OTHER FILE IN DIFF
[DO DIFF CHANGES]
:diffoff                        TURN DIFF OFF

### OTHER KEYBINDINGS
.vimrc
   map ] ]c
   map [ [c


To limit this action to diff mode, use following
(highlight colors are modified to fit my particular background, you may ignore hi commands and set cursorline) 
if &diff
    set cursorline
    map ] ]c
    map [ [c
    hi DiffAdd    ctermfg=233 ctermbg=LightGreen guifg=#003300 guibg=#DDFFDD gui=none cterm=none
    hi DiffChange ctermbg=white  guibg=#ececec gui=none   cterm=none
    hi DiffText   ctermfg=233  ctermbg=yellow  guifg=#000033 guibg=#DDDDFF gui=none cterm=none









### more suggestions @TEST: 
The default identifiers that can be selected using diffget
LO local master copy
RE remote master to be merged
BA common ancestor of remote and local changes.

You can influence how many identical lines are kept around changes (default: 6 lines above and below) via the context value of the diffopt option. So, to completely fold all identical lines:

:set diffopt+=context:0



### vim-diff-enhanced plugin

in Diff mode
:EnhancedDiff histogram

ignoring parts of file
:EnhancedDiffIgnorePat <pattern>

use patience diff algorithm
:PatienceDiff

choose diff algorithms
:EnhancedDiff [agorithm]
> myers Default Diff algorithm used
> default Alias for myers algorithm
> histogram Fast version of patience algorithm
> minimal Default diff algorithm, trying harder to minimize the diff
> patience Patience diff algorithm.

turn off
:EnhancedDiffDisable





## SEARCH COMMANDS AND PATTERNS
### SEARCH LINKS
https://vim.help/27-search-commands-and-patterns
https://vim.fandom.com/wiki/Highlight_all_search_pattern_matches


#### Search Patterns

| \<wholeWHord\> | whole word search | 
|  \<i           | words that start with i|
| ' i>\ '        |  words taht start with i |
| ' > \ '        | adds an or to the search |
               

 asdkjf;asldkjf< > asdlfkjasd;lkfjas
 a;lsdkjf;asldkjf
> a;lskdjf;laskdjf
> alsdkjf;laskdjf;lsadkj
> as;ldkfj;asldkjf
> a;lsdkfj;alskdjf;lk
> a;sldkfj;asldkfj
> a;sdlkfj;asldkfj
> asl;dkfj;aslkdfj
> a;lsdkfj;asldkjf\>
>
>


@FIXME: @VSCODE: @!VIM:





\(\<\w\+\>\)\_s*\<\1\>
pattern searches for \<\w\+\> (word beginning \<, word character \w, one or more \+ word characters, word end \>). That is, it searches for a whole word. It then looks for any amount of whitespace (\_s*); \s matches space or tab, while \_s matches space or tab or newline (end-of-line character). Finally, the pattern looks for \1 which is the whole word that was found in the escaped parenthese


search for red green or blue
red\|green\|blue


To replace all instances of "red" or "green" or "blue" with "purple", enter: 
:%s/red\|green\|blue/purple/g


However, the above pattern finds "red" in "bored", so the substitute would change "bored" to "bopurple". If that is not what you want, use the following pattern to find only the whole words "red" or "green" or "blue":

\<\(red\|green\|blue\)\>

In a pattern, \< and \> respectively specify the beginning and end of a word, while \( and \) respectively specify the beginning and end of a group (the pattern \<red\|green\|blue\>, without escaped parentheses, would find "red" occurring at the beginning of a word, or "green" occurring anywhere, or "blue" occurring at the end of a word). 













### Options
:set ignorecase
:set noignorecase
:set ignorecase smartcase

highlghting search terms
:set hlsearch
:et ohlsearch


| PATTERN | MATCHES|
|--------| --------|
| word	    | word, Word, WORD, WoRd, etc.|
| Word	    | Word |
| WORD	    | WORD |
| WoRd	    | WoRd |




