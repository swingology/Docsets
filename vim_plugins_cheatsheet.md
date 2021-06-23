# VIM PLUGIN CHEATSHEET

## TODO
- [ ] shift tab in zshell ~ FZF?
-

## TOC

<!-- vim-markdown-toc GitLab -->

* [LINKS](#links)
    * [customization link](#customization-link)
* [CHEATSHEETS](#cheatsheets)
    * [VIM QUICKKEYS GH LINKS](#vim-quickkeys-gh-links)
    * [FZF](#fzf)
    * [FLOATTERM](#floatterm)
    * [VIM-MARKDOWN](#vim-markdown)
    * [VIM MULTIPLE CURSORS](#vim-multiple-cursors)
    * [VIM-MARKDOWN](#vim-markdown-1)
    * [vim-markdown-toc](#vim-markdown-toc)

<!-- vim-markdown-toc -->
## LINKS

-------

- [vim-markdown-toc](https://github.com/mzlogin/vim-markdown-toc)
  - [vim markdown toc - OPTIONS](https://github.com/mzlogin/vim-markdown-toc#options)
  - [vim markdonw toc - USAGE](https://github.com/mzlogin/vim-markdown-toc#usage)
-[ Vim Airline GH page](https://github.com/vim-airline/vim-airline )
### customization link

https://vim.fandom.com/wiki/Avoid_the_escape_key

------

## CHEATSHEETS
| VIM | 
| shift-k | opens split of manual of word under cursor| 


### VIM QUICKKEYS [GH LINKS](vim_cheats) 
| mode | keys           | alt keys                           | actions | LINUX | MBP | Mini | MBA |
| ---- | -------------- | ---------------------------------- | ------- | ----- | --- | ---- | --- |
| n/v  | I              | insert mode - at beginning of line |         |       |     |      |     |
| n/v  | shft + up/down | Go top/bottom of page              |         |       |     | x    |     |


### FZF 

| shift = up/down | scroll the preview window from bat | 




### FLOATTERM
[Floatterm Use Guide](https://github.com/voldikss/vim-floaterm#get-started)

| :FloatermNew | Start a new term | :FloatermNew python







### VIM-MARKDOWN
[Vim-Markdown GH Page]https://github.com/plasticboy/vim-markdowni(



| [[ or ]] | move to next or prev header |  n/v |
| [] or ][ | prev sibling or next sibling header | n/v |
| ]c | go to current header | n/v |
| ]u | go to parent header | n/v |




| CHANGING CASES | | | | | | | | 
 ~    : Changes the case of current character

 guu  : Change current line from upper to lower.

 gUU  : Change current LINE from lower to upper.

 guw  : Change to end of current WORD from upper to lower.

 guaw : Change all of current WORD to lower.

 gUw  : Change to end of current WORD from lower to upper.

 gUaw : Change all of current WORD to upper.

 g~~  : Invert case to entire line

 g~w  : Invert case to current WORD

 guG  : Change to lowercase until the end of document.

 gU)  : Change until end of sentence to upper case

 gu}  : Change to end of paragraph to lower case

 gU5j : Change 5 lines below to upper case

 gu3k : Change 3 lines above to lower case




<C-n> (ctrl + n )

_____

### VIM MULTIPLE CURSORS

https://github.com/terryma/vim-multiple-cursors
<C-n> toggle multiple cursors 
general workflow
go into visual mode
select all lines you want a cursor
<C-n> (ctrl + n )

### VIM-MARKDOWN

@cursors: @olding: 

| Keystrokke | action                                     |
| ---------- | ------------------------------------------ |
| zr         | reduces fold level throughout the buffer   |
| zR         | opens all folds                            |
| zm         | increases fold level throughout the buffer |
| zM         | folds everything all the way               |
| za         | open a fold your cursor is on              |
| zA         | open a fold your cursor is on recursively  |
| zc         | close a fold your cursor is on             |
| zC         | close a fold your cursor is on recursively |

### vim-markdown-toc

| MODE                                 | COMMAND          | ACTION                                                     |     |     |
| ------------------------------------ | ---------------- | ---------------------------------------------------------- | --- | --- |
| C                                    | :GenTocGitlab    | Generate TOC in GitLab style                               |     |     |
| C                                    | :GenTocGFM       | Generate TOC in GFM link style                             |     |     |
| C                                    | :GenTocRedcarpet | Generate TOC in Redcarpet style                            |     |     |
| C                                    | :GenTocMarked    | Generate TOC in Markedlink style                           |     |     |
| ***\*update\**** && ***\*remove\**** |                  |                                                            |     |     |
| C                                    | :UpdateToc       | Updates TOC when g:vmt_autoupdate_on_save is ***\*off\**** |     |     |
| C                                    | :GenTocGitlab    | Generrate TOC in GitLab style                              |     |     |
|                                      |                  |                                                            |     |     |
