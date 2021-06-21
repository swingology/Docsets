# Vim CheatSheet

## TOC

<!-- vim-markdown-toc GitLab -->

	* [EASY BEST ACTIONS](#easy-best-actions)
	* [VIM SPLITS - PANE](#vim-splits-pane)
	* [VIM PANES](#vim-panes)
	* [SELECTION](#selection)
	* [BEST-ACTIONS](#best-actions)
	* [DEFAULT SHORTCUTS](#default-shortcuts)
	* [LINKS](#links)
		* [PLUGINS](#plugins)
* [#### REGISTERS](#-registers)
	* [RIL](#ril)

<!-- vim-markdown-toc -->


### EASY BEST ACTIONS



|COMMAND|mode |ACTION | EX |
|----|---|---|---|
|  b  | n | move to beginning of previous word | | 
| $ | n | move to beginning of line | | 
| g  _ | n  | move to last non blank char of line | |  
| _ | n  |  move to first non blank char of line | | 

shift l m h 
| i	| ctrl h 	| backspace ||
| **BUFFERS PANES TABS** | | | |
| c | :ls | list buffers | | 
| i | a | append - moves cursor after current to insert mode | | 
| i | o | inserts new line|  | 
| i | I | beginning of line and INSERT MODE | |
| i | a | end of line and INSERT MODE | | 
| i | O | inserts new line and INSERT MODE | |


| nv |   | 
115



### VIM SPLITS - PANE


|MODE |COMMAND |ACTION | EX |
|----|---|---|---|
| c | :q| quit | | 

| RESIZING SPLITS| |||

| N/V/
| c | :vsp <file path>| open vertical split|
| c | :sp <$file> | open horizontal split|
| c | <num>:sp <<file> | open h split with split height | 




### VIM PANES



### SELECTION


### BEST-ACTIONS


### DEFAULT SHORTCUTS

:ls - open buffer list 
https://www.reddit.com/r/vim/comments/g4l5p0/good_plugin_to_navigate_buffers/
nnoremap <leader>b :ls<CR>:b to change
<leader>n :bn<CR> <leader>p :bp<CR>
nnoremap ,n :bn<CR> 
nnoremap ,b :bp<CR>
nnoremap ,h :b#<CR>

### LINKS

[remap, noremape, nnoremap, vnoremap](https://stackoverflow.com/questions/3776117/what-is-the-difference-between-the-remap-noremap-nnoremap-and-vnoremap-mapping)
[recording keys for repeated jobs](https://vim.fandom.com/wiki/Recording_keys_for_repeated_jobs
[<leader> in vimrc](https://stackoverflow.com/questions/1764263/what-is-the-leader-in-a-vimrc-file)


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
