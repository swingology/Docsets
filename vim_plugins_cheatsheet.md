:

# TOC

## Links

-------

- [vim-markdown-toc](https://github.com/mzlogin/vim-markdown-toc)
  - [vim markdown toc - OPTIONS](https://github.com/mzlogin/vim-markdown-toc#options)
  - [vim markdonw toc - USAGE](https://github.com/mzlogin/vim-markdown-toc#usage)

#### customization link

https://vim.fandom.com/wiki/Avoid_the_escape_key

------

## Cheatsheets

=================

| mode | keys           | alt keys                           | actions | LINUX | MBP | Mini | MBA |
| ---- | -------------- | ---------------------------------- | ------- | ----- | --- | ---- | --- |
| n/v  | I              | insert mode - at beginning of line |         |       |     |      |     |
| n/v  | shft + up/down | Go top/bottom of page              |         |       |    | x    |     |

<C-n> (ctrl + n )

_____

### vim multiple cursors

https://github.com/terryma/vim-multiple-cursors
<C-n> toggle multiple cursors 
general workflow
go into visual mode
select all lines you want a cursor
<C-n> (ctrl + n )

### vim-markdown

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
