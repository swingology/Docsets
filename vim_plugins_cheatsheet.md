# VIM PLUGIN CHEATSHEET

## TODO
- [ ] shift tab in zshell ~ FZF?
-

## Plugins Most Used Commands

:GitGutterEnable
:GitGutterDisable
:GitGutterToggle


Markdown Plugin
:Toc
:TableFormat
:InsertToc {n}  - display up to headers h{n} (n is an int)
:InsertNToc
]]              - go to next header
[[              - go to previous header
][              - go to next sibling
[]              - go to previous sibling
]c              - go to current header
]u              - go to parent header 



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
    * [gitgutter](#gitgutter)
* [VIM CUSTOMIZATION VIMRC](#vim-customization-vimrc)

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



### COC
https://github.com/neoclide/coc.nvim/wiki/Install-coc.nvim
https://github.com/neoclide/coc.nvim/wiki/Using-coc-extensions

:CocInfo
:CocInstall <extensions>
:CocCommand <tab>               - command completion

:CocList commands
:CocUninstall <extensions>
:CocList extensions             - list coc extensions




### FLOATTERM
[Floatterm Use Guide](https://github.com/voldikss/vim-floaterm#get-started)

| :FloatermNew | Start a new term | :FloatermNew python







### VIM-MARKDOWN
[Vim-Markdown GH Page](https://github.com/plasticboy/vim-markdown)

| :TableFormat | cleanup table|
| :Toc | create vertical splt window with TOC | 
| :InsertToc | Create TOC where cursor is | 
| [[ or ]] | move to next or prev header |  n/v |
| [] or ][ | prev sibling or next sibling header | n/v |
| ]c | go to current header | n/v |
| ]u | go to parent header | n/v |
| **MAPPINGS**|
| ge | follow link under cursor from vim| n/v|
| gx | open link under cursor as standard gx | n/v/|


| CHANGING CASES | | | | | | | | 
 ~    : Changes the case of current character
 guu  : Change current line from upper to lower.
 gUU  : Change current LINE from lower to upper.
 guw  : Change to end of current WORD from upper to lower.
 guaw : Change all of current WORD to lower.
 gUw  : Change to end of current WORD from lower to upper.
 gUaw : Change all of current WORD to upper.
 g ~ ~  : Invert case to entire line
 g ~ w  : Invert case to current WORD
 guG  : Change to lowercase until the end of document.
 gU)  : Change until end of sentence to upper case
 gu}  : Change to end of paragraph to lower case
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
@vimmd: @plugin:
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





### gitgutter
@plugins: @vim: @git: @gitgutter:
https://github.com/airblade/vim-gitgutter

'in vimrc'
let g:gitgutter_max_signs = 500 'default value'
nmap ]h <Plug>GitGutterNextHunk
nmap [h <Plug>GitGutterPrevHunk

ijump to git hunk
]c or [c

nmap ]h <Plug>GitGutterNextHunk
nmap [h <Plug>GitGutterPrevHunk

map ghs <Plug>(GitGutterStageHunk)
nmap ghu <Plug>(GitGutterUndoHunk)

nmap ghp <Plug>(GitGutterPreviewHunk)

set foldtext=gitgutter#fold#foldtext()




You can stage or undo an individual hunk when your cursor is in it:

    stage the hunk with <Leader>hs or
    undo it with <Leader>hu.

To stage part of an additions-only hunk by:

    either visually selecting the part you want and staging with your mapping, e.g. <Leader>hs;
    or using a range with the GitGutterStageHunk command, e.g. :42,45GitGutterStageHunk.

To stage part of any hunk:

    preview the hunk, e.g. <Leader>hp;
    move to the preview window, e.g. :wincmd P;
    delete the lines you do not want to stage;
    stage the remaining lines: either write (:w) the window or stage via <Leader>hs or :GitGutterStageHunk.



## VIM CUSTOMIZATION VIMRC


https://stackoverflow.com/questions/3074068/how-to-change-the-color-of-the-selected-code-vim-scheme

** Visual Line and Visual Block Coloring**
  hi CursorLine guibg=#DDDDDD gui=none
  hi CursorColumn guibg=#EEEEEE gui=none
  hi MatchParen guifg=#f6f3e8 guibg=#857b6f gui=none
  hi Pmenu   guifg=#f6f3e8 guibg=#DDDDDD gui=none
  hi PmenuSel  guifg=#000000 guibg=#DDDDDD gui=none
endif

" General colors
hi Cursor   guifg=NONE    guibg=#656565 gui=none
hi Normal   guifg=#000000 guibg=#FFFFFF gui=none
hi NonText   guifg=#808080 guibg=#FFFFFF gui=none
hi LineNr   guifg=#857b6f guibg=#FFFFFF gui=none
hi StatusLine  guifg=#000000 guibg=#FFFFFF gui=none
hi StatusLineNC guifg=#857b6f guibg=#FFFFFF gui=none
hi VertSplit  guifg=#444444 guibg=#FFFFFF gui=none
hi Folded   guibg=#AAAAAA guifg=#FFFFFF gui=none
hi Title  guifg=#000000 guibg=NONE gui=none
hi Visual  guifg=#000000 guibg=#FFFFFF gui=none
hi SpecialKey guifg=#808080 guibg=#FFFFFF gui=none

hi Visual  guifg=#000000 guibg=#FFFFFF gui=none


######################## ****************************************************
