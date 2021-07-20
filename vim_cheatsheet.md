# Vim CheatSheet

## TODO
    - [ ] can you put buffer in a split
    - [ ] can you put a buffer in a popup - :Buf or :Buffers in fzf
    -



## TOC

<!-- vim-markdown-toc GitLab -->

    * [EASY BEST ACTIONS](#easy-best-actions)
    * [VIM SPLITS - PANE](#vim-splits-pane)
        * [VIM Splits Customization](#vim-splits-customization)
    * [VIM BUFFERS](#vim-buffers)
        * [Buffer Link](#buffer-link)
    * [SELECTION](#selection)
    * [SEARCHING](#searching)
        * [Basic Search](#basic-search)
        * [Searching Links](#searching-links)
    * [HIGHLIGHTING](#highlighting)
        * [Links](#links)
    * [BEST-ACTIONS](#best-actions)
    * [DEFAULT SHORTCUTS](#default-shortcuts)
    * [BOOKMARKS](#bookmarks)
    * [LINKS](#links-1)
        * [PLUGINS](#plugins)
* [#### REGISTERS](#-registers)
    * [RIL](#ril)
    * [CLEARING UP VIM PLUGINS](#clearing-up-vim-plugins)

<!-- vim-markdown-toc -->

### Daily addisiont
| <s-r> Replace mode | n | 
| <s-p> paste in line above | n |
| <s-p> replace line | v-line |
| <s-w> | move to beginning of next word | n v |
| e | move to end of next word | n v |
| w | move to next beginning of word | n v | 








### EASY BEST ACTIONS

| :h term | search help for term | C |

| COMMAND    | MODE | ACTION                               | TAGS     | APP   |
| ---------- | ---- | ------------------------------------ | -------- | ----- |
| **NAVIGATION** |  |                                      |          |       |
| b          | n    | move to beginning of previous word   | @cursor: | @vim: |
| '\$'       | n    | move to end of line **MEANS JSUT DOLLAR SIGN**  | @cursor: | @vim: |
| g  _       | n    | move to last non blank char of line  | @cursor: | @vim: |
| _          | n    | move to first non blank char of line | @cursor: | @vim: |
| w or W     | n v  | move to beginning of word                                     |          |       |





shift l m h 
| i	| ctrl h 	| backspace ||
| **BUFFERS PANES TABS** | | | |
| c | :ls | list buffers | | 
| :vert sb#  | opens buffer # in vsplit  | 
| :vsp sb#   | opens buffer # in vsplit  | 
| :sp sb# | opens buffer # in hsplit    |

|NAVIGATION| ||||
| i | a | append - moves cursor after current to insert mode | | 
| i | o | inserts new line|  | 
| i | I | beginning of line and INSERT MODE | |
| i | a | end of line and INSERT MODE | | 
| i | O | inserts new line and INSERT MODE | |







### VIM SPLITS - PANE


|COMMAND |ACTION | MODE | TAGS | APP |
|----|---|---|---|----|
|:vsp {file} | open file in vsp | c | | | 
|:sp or :hsp {file} | open file in hsp | c | | |
|:q | close pane | c | | |
| RESIZING SPLITS |     |   |   | |
| ctrl-w +/- | increases/decreases current horiz split by 1 line | n | | | 
| ctrl-w </> | increases/decrease current vert split by 1 line | n | | |
| ctrl-w <num>+{+,-,<,>}    | increases current pane by num | n | | |
| ctrl-w shft-'-'(_) | cur pane maximize horiz | n | | |
| ctrl-w shft-\(|) | cur pane maximize vert | n | | |
| ctrl-w = | make all panes equal | n | | |
| [N]ctrl-w {-,+,<,>} | change width or height by N chars | n | | |
| :vertical resize 30 | resize current pane to 30 chars wide | c | | |
| :30winc + or - | 30 more/less chars high | c | | |
| :30winc > or :30winc < | 30 more/less chars wide | c | | |
| :res <N>            | set curent window to N rows | c | | |
| :vsp <file path>i | open vertical split| c | | |
| :sp <file> | open horizontal split| c | | |
| <num>:sp <file> | open h split with split height | c | | |
| <num>:vsp <file> | open v split with split width | c | | |
| :set scrollbind or scb | scroll the panes together | c | | | 
| :set scb! | turn off scroll bind| | | | 

| ctrl -w shft h/j/k/l | change split configurations | n|

#### VIM Splits Customization
``` bash
" Switch between window splits using big J or K and expand the split to its
" full size.
"
" Move vertically in the window through the horizontal splits...
map <C-J> <C-w>j<C-w>_
map <C-K> <C-w>k<C-w>_

" Move horizontally in the window through the vertical splits...
map <C-H> <C-w>h<C-w>\|
map <C-L> <C-w>l<C-w>\|
```
``` bash
nmap 7 :res +2<CR> " increase pane by 2 
nmap 8 :res -2<CR> " decrease pane by 2
nmap 9 :vertical res +2<CR> " vertical increase pane by 2
nmap 0 :vertical res -2<CR> " vertical decrease pane by 2

```


``` bash
" ALT → will increase width of the selected split
" ALT ← will decrease width of the selected split
" ALT ↓ will increase height of the selected split
" ALT ↑ will decrease height of the selected split

nmap <M-Right> :vertical resize +1<CR>
nmap <M-Left> :vertical resize -1<CR>
nmap <M-Down> :resize +1<CR>
nmap <M-Up> :resize -1<CR>

```




### VIM BUFFERS


| COMMAND | MODE | ACTION                               | TAGS | APP |
|---------|------|--------------------------------------|------|-----| 
| :ls or :buffers | list buffers | c | | |  
| :vert sb#  | opens buffer # in vsplit  | c | | |
| :vsp sb#   | opens buffer # in vsplit  | c | | | 
| :sp sb# | opens buffer # in hsplit    | c | | | 
| :Buf or :Buffers | FZF list buffers | c | | | 
| :e <#> or :edit <file> | create buffere with file | c | | |
| :new | new buffer - split horiz | 
| :vnew | new buffer - split vert   |
| :b <num> or buffer <num> | display buffer with <num> | c | | | 
| :bd   | delete buffer, fail if unsaved | c | | | 
| :bd! | force delete buffer | c | | |
| :ball | load all buffers in split windows | 
| :vertical ball | load all buffers in v split windows | 
| :sbuffer <num> | open buffer num in new window | 
| :bdelete buf1 buf2 ... | delete buf1 and buf2 |
| :2,4bdelete | delete buffers from 2 to 4|
| :bbad <file> | add a new buffer - not open 

:sball :unhide :sunhide
:bfirst :brewind :bprevious :bNext
:sbfirst :sbrewind :sbnext :sbprevious :sbNext

:vertical sb 3
    Create a vertical split and show buffer number 3 in the window to the left.

:vertical rightbelow sfind file.txt
    Create a vertical split and read file.txt into the buffer in the right window.

:rightbelow sfind file.txt

:map <buffer> ,w /[.,;]<CR>
:abb <buffer> FF for (i = 0; i < ; ++i)



#### Buffer Link
https://github.com/jlanzarotta/bufexplorer
https://medium.com/@Sohjiro/introduction-to-vim-buffers-dd966ff518d

http://vimdoc.sourceforge.net/cgi-bin/help?tag=map-local
http://vimdoc.sourceforge.net/cgi-bin/help?tag=abbreviate-local








### SELECTION


### SEARCHING
#### Basic Search
@vim: @search: @
| COMMAND | ACTION | MODE | TAGS | APP | 
|---|---|---|---|---|
| * over word | search forward for word under cursor | n |
| # over word | search backwards for word under cursor | n|
| /_pattern  | search pattern forwards |
| ?_pattern | search pattern backwards |
| /\<WORD\>  | searches for exact WORD match |
| “gnu” you would use /\<gnu\> ||
| After search|
| n | find next occurence | 
| N | find previous occurence |
| :set ic or ignorecase | sets case insensitive search (command line or vimrc) i|
| /Word\c  | search for Word case insensitve |
| /Word\C  | search for Word case match search |

#### Searching Links
https://vim.fandom.com/wiki/Searching




### HIGHLIGHTING
uses matchadd()

The script defines highlight groups named hl1, hl2, ... hl9 (and more). Once enabled, pressing one of the keys 1, 2, ... 9 on the numeric keypad will highlight the word under the cursor with the colors defined in the corresponding highlight group (for example, press 4 on the keypad to highlight the current word with the hl4 group). 
 
 #### USAGE

\m //if m is <leader>



#### Links
- [ ] https://vim.fandom.com/wiki/Highlight_multiple_words
- [ ] https://vim.fandom.com/wiki/Highlight_all_search_pattern_matches @todo:
- [ ] http://vimcasts.org/episodes/operating-on-search-matches-using-gn/ @todo:



### BEST-ACTIONS


### DEFAULT SHORTCUTS

:ls - open buffer list 

``` bash
" https://www.reddit.com/r/vim/comments/g4l5p0/good_plugin_to_navigate_buffers/
nnoremap <leader>b :ls<CR>:b 
" to change
<leader>n :bn<CR> <leader>p :bp<CR>
nnoremap ,n :bn<CR> 
nnoremap ,b :bp<CR>
nnoremap ,h :b#<CR>
```


### BOOKMARKS
| Shortcut             | Action                                                 | Mode   |
| ------               | ------                                                 | ------ |
| m{bookmarkname}      | create bookmark                                        | nv     |
| `<bookmark name>     | move to exact location of bookmark                     | nv     |
| '<bookmark name>     | move to beginning of line of bookmark                  | nv     |
| :marks               | list all bookmarks                                     | c      |
| :delmarks <bookmark> | delete bookmark                                        | c      |
| d'<markname>         | delete everthing between currnet position and markline |        |
ma 	set mark a at current cursor location
'a 	jump to line of mark a (first non-blank character in line)
`a 	jump to position (line and column) of mark a
d'a 	delete from current line to line of mark a
d`a 	delete from current cursor position to position of mark a
c'a 	change text from current line to line of mark a
y`a 	yank text to unnamed buffer from cursor to position of mark a
:marks 	list all the current marks
:marks aB 	list marks a, B
]' 	jump to next line with a lowercase mark
[' 	jump to previous line with a lowercase mark
]` 	jump to next lowercase mark
[` 	jump to previous lowercase mark 
If you wipeout a buffer (command :bw), all marks for the buffer are deleted.



The :delmarks command (abbreviated as :delm) may be used to delete specified marks.
Command 	Description
:delmarks a 	delete mark a
:delmarks a-d 	delete marks a, b, c, d
:delmarks abxy 	delete marks a, b, x, y
:delmarks aA 	delete marks a, A
:delmarks! 	delete all lowercase marks for the current buffer (a-z)


|                      |                                                        |        |
NOTE: Capital Mark can only exist in one file. A mark can only exist in one openn file. a bookmark can be on all open files


### LINKS

[remap, noremape, nnoremap, vnoremap](https://stackoverflow.com/questions/3776117/what-is-the-difference-between-the-remap-noremap-nnoremap-and-vnoremap-mapping)
[recording keys for repeated jobs](https://vim.fandom.com/wiki/Recording_keys_for_repeated_jobs
[<leader> in vimrc](https://stackoverflow.com/questions/1764263/what-is-the-leader-in-a-vimrc-file)
[Using marks and perform vim selection](https://www.howtoforge.com/tutorial/how-to-use-markers-and-perform-text-selection-in-vim/)
#### PLUGINS
https://github.com/mg979/vim-yanktools
https://github.com/liuchengxu/vim-which-key




#### REGISTERS
-------
[vim registers - the basics and beyond](https://www.brianstorti.com/vim-registers/)
Registers

    :reg[isters] - show registers content
    "xy - yank into register x
    "xp - paste contents of register x
    "+y - yank into the system clipboard register
    "+p - paste from the system clipboard register


------
### RIL

-----
detab and tab customization
Vim already has built-in key commands for insert mode to shift the current line left or right one &shiftwidth. They are (in insert mode):

Ctrl-t : shift right (mnemonic "tab")

Ctrl-d : shift left (mnemonic "de-tab")

If you still want to use shift-tab, this is how you do it:

" for command mode
nnoremap <S-Tab> <<
" for insert mode
inoremap <S-Tab> <C-d>



----




### CLEARING UP VIM PLUGINS
https://mkaz.blog/working-with-vim/plugins/

**Removing Plugin**
1. remove from .vimrc
2. in vim ':PlugClean'

**Updating Plugin**
:PlugUpdate

**Upgrade vim-plug**
:PlugUpgrade
