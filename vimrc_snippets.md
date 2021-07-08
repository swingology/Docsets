



command to open current buffer in vsplit
``` bash

command -nargs=1 Vsb call VsbFunction(<f-args>)

function VsbFunction (arg1)
  execute 'vert sb' a:arg1
endfunction

# to call 
# :Vsb somefile
```




" changing popup background :help highlight-groups
" :highlight Pmenu ctermbg=gray guibg=gray
" Pmenu : PmenuSel : PmenuSel : PmenuThumb : ctermbg or ctermfg or cterm
" http://vimhelp.appspot.com/syntax.txt.html#highlight-ctermfg
":h highlight-ctermfg
"https://vi.stackexchange.com/questions/22278/why-my-vim-doesnt-support-hex-color-code
"https://vi.stackexchange.com/questions/12664/is-there-any-way-to-change-the-popup-menu-color






## VIM SCRATCH
@scratch: @vimrc:


# CUT OUT of NVIM init.vimrc


" Plug 'lambdalisue/vim-gista'

" Plug 'lambdalisue/vital-Web-API-GitHub' 
" Plug 'Shougo/unite.vim'


"filetype plugin on

"call plug#begin('~/.config/nvim/plugged')
"Plug 'mkitt/tabline.vim'
"Plug 'liuchengxu/vim-clap', { 'do': ':Clap install-binary' }
"Plug 'tpope/vim-fugitive'
"call plug#end()


" Plug 'szymonmaszke/vimpyter'
" Plug 'lambdalisue/vim-gita'
" Plug 'lambdalisue/vital-ArgumentParser'
" Plug 'lambdalisue/vital-Vim-Prompt'
" Plug 'lambdalisue/vital-Vim-Validate'
" Plug 'lambdalisue/vital-Vim-Buffer-Anchor'


" Plug 'rudylee/nvim-gist' " , { 'do': ':UpdateRemotePlugins' }
" Plug 'mattn/gist-vim'
" Plug 'mattn/webapi-vim'
" Plug 'liuchengxu/vim-which-key', { 'on': ['WhichKey', 'WhichKey!'] }



" TABLINE
"let g:tablineclosebutton=1
"hi TabLine      ctermfg=Black  ctermbg=Grey     cterm=NONE
"hi TabLineFill  ctermfg=Black  ctermbg=Grey     cterm=NONE
"hi TabLineSel   ctermfg=White  ctermbg=Blue     cterm=NONE


