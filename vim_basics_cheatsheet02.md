# 

TOC
---


### HELP
| keys | action | mode | ex |
|------| ------ | ---- | -- |
| :help | help | c | | 
| :help <command> | help for command | c | :help tags Ctrl d and tab | 

For example, try :help tags (then CTRL-d and TAB)
Do help i_ CTRL-d for insert commands, v_ for visual, etc.
Also, when in the help pages, CTRL-] jumps to subjects between |bars| and CTRL-T jumps back (and, of course, :q to quit
_____

### VARIABLES
:set            - shows vars different from defaults
:set all        - shows all values
:set foo?       - shows the value of foo
:set foo+=opt   - add opt to the value w/o changing others
:set foo-=opt   - remove opt from value
:set foo&       - reset foo to default value
:setlocal foo   - only the current buffer
____

### WORD & LINE COMPLETION
| ctrl n / ctrl p | i | next/prev word completion | |
| ctrl x ctrl l (ctrl-n/p) | i | line complettion | | 
| :set dictionary=/usr/share/dict/words | | | 
| ctrl-x ctrl-k | i | dictionary completion | |
| **ERASE** | | | 
| ctrl-w | i | erase word | | 
| ctrl-u | i | erase line | 

_____

### **SEARCHING**
 For basic searching:

/pattern       - search forward for pattern
?pattern       - search backward
n              - repeat forward search
N              - repeat backward

Some variables you might want to set:

:set ignorecase - case insensitive
:set smartcase  - use case if any caps used
:set incsearch  - show match as search proceeds
:set hlsearch   - search highlighting

More cool searching tricks:

*               - search for word currently under cursor
g*              - search for partial word under cursor
                  (repeat with n)
ctrl-o, ctrl-i  - go through jump locations
[I              - show lines with matching word under cursor

Search and replace...

:%s/search_for_this/replace_with_this/    - search whole file and replace
:%s/search_for_this/replace_with_this/c   - confirm each replace

_____
### **TEXT SELECTION**
If you want to do the same thing to a collection of lines, like cut, copy, sort, or format, you first need to select the text. Get out of insert mode, hit one of the options below, and then move up or down a few lines. You should see the selected text highlighted.

V       - selects entire lines
v       - selects range of text
ctrl-v  - selects columns
gv      - reselect block

After selecting the text, try d to delete, or y to copy, or :s/match/replace/, or :center, or !sort, or...

Here's one way to move selected text over a few spaces:

 - select a chunk of code using capital V and the arrow keys (or j, k)
 - type colon
 - then type s/^/   /
 - hit return

What you've done is replace the beginning of each selected line (the ^ symbol means "the beginning of the line") with spaces.

_____

### **MARKERS**
Use markers to set places you want to quickly get back to, or to specify a block of text you want to copy or cut.

 mk      - mark current position (can use a-z)
 'k      - move to mark k
 d'k     - delete from current position to mark k
 'a-z    - same file
 'A-Z    - beteween files|


_____
### **INDENTING**

Some variables you might want to set:

 :set tabstop=8     - tabs are at proper location
 :set expandtab     - don't use actual tab character (ctrl-v)
 :set shiftwidth=4  - indenting is 4 spaces
 :set autoindent    - turns it on
 :set smartindent   - does the right thing (mostly) in programs
 :set cindent       - stricter rules for C programs

I like having auto on, but smart does funny things based on keywords.

To indent the current line, or a visual block:

ctrl-t, ctrl-d  - indent current line forward, backwards
                  (insert mode)
visual > or <   - indent block by sw (repeat with . )

To stop indenting when pasting with the mouse, add this to your .vimrc:

:set pastetoggle=<f5>

then try hitting the F5 key while in insert mode (or just :set paste).


_____

### **REFORMATTING**

Some variables you might want to set:

 :set tabstop=8     - tabs are at proper location
 :set expandtab     - don't use actual tab character (ctrl-v)
 :set shiftwidth=4  - indenting is 4 spaces
 :set autoindent    - turns it on
 :set smartindent   - does the right thing (mostly) in programs
 :set cindent       - stricter rules for C programs

I like having auto on, but smart does funny things based on keywords.

To indent the current line, or a visual block:

ctrl-t, ctrl-d  - indent current line forward, backwards
                  (insert mode)
visual > or <   - indent block by sw (repeat with . )

To stop indenting when pasting with the mouse, add this to your .vimrc:

:set pastetoggle=<f5>

then try hitting the F5 key while in insert mode (or just :set paste).


_____

### **FOLDING** 
Use folds to collapse selected blocks. Useful if you've finished a subroutine and want to save window space, or maybe want to fold all blocks of comments.

    select block, then :fold
    zo - open
    zc - close

See :help foldmethod for options, and use :mkview and :loadview to save and restore the current window.


___

### MULTIPLE WINDOWS

If you want, you can probably do everything from one vim session! :) Here are some commands to turn one vim session (inside one xterm) into multiple windows.

 :e filename      - edit another file
 :split filename  - split window and load another file
 ctrl-w up arrow  - move cursor up a window
 ctrl-w ctrl-w    - move cursor to another window (cycle)
 ctrl-w_          - maximize current window
 ctrl-w=          - make all equal size
 10 ctrl-w+       - increase window size by 10 lines
 :vsplit file     - vertical split
 :sview file      - same as split, but readonly
 :hide            - close current window
 :only            - keep only this window open
 :ls              - show current buffers
 :b 2             - open buffer #2 in this window

___
### EDITING IN A STREAM
You can take the output of any command and send it into a vim session. From there you could format it, change stuff, and then save it to a file.

find . | vim - 

____
### TAGS
Using tags makes it easier to jump to certain parts of your programs. First run ctags from the UNIX command line on your source files (e.g., ctags prog.c or ctags -R to recurse) to generate a "tags" file, then use these while editing your source files:

 :tag TAB            - list the known tags
 :tag function_name  - jump to that function
 ctrl-t   - goes to previous spot where you called :tag
 ctrl-]   - calls :tag on the word under the cursor
 :ptag    - open tag in preview window (also ctrl-w })
 :pclose  - close preview window

_____
### MAKEFILES
 Using makefiles can save time when compiling lots of source files into one program. vim can run the makefile without leaving the editing session:

 :map <f9> :make    - map the F9 key to run make
 :set makeprg       - change what :make does

:make will compile if you are using a Makefile. Use these to examine the compile errors:

 :copen    - open a mini-window with list of errors
           - hit enter on an error to jump to line
 :cclose   - closes the mini-window
 :cw       - toggles the mini-window (if errors exist)

_____ 
### MAPPING
 Use mappings to save typing for things you frequently type. The first one below, when typing in insert mode, changes every occurence of ;so to System.out.println(); and leaves you in insert mode between the parentheses!

 imap ;so System.out.println();<left><left>
 imap ;ne <esc>/;<cr>a
 vmap <buffer> ;bo "zdi<B><c-r>z</B><esc>

The second one above, while in insert mode, moves you to the end of the next line when you type ;ne. The last one puts bold html tags around something you have visually selected.

These usually go in your .vimrc file. You can even have certain mappings loaded based on the type of file you are editing.

Quiz: what do these do? :)

nnoremap <F6> <C-W>w
nnoremap <S-F6> <C-W>W

map <C-L> :noh<CR>:redraw!<CR>


____
### REGISTER
 When you copy and cut stuff, it gets saved to registers. You can pull stuff from those registers at a later time.

 :reg     - show named registers and what's in them
 "5p      - paste what's in register "5

You can also record a whole series of edits to a register, and then apply them over and over.

 qk       - records edits into register k 
            (q again to stop recording)
 @k       - execute recorded edits (macro)
 @@       - repeat last one
 5@@      - repeat 5 times

 "kp      - print macro k 
            (e.g., to edit or add to .vimrc)
 "kd      - replace register k with what cursor is on

_____
### SPELLING
This is a good place to learn about plugins. Go to www.vim.org, click on the Search link, search the scripts for spelling, and then download the vimspell.vim plugin. To install it, put it in your ~/.vim/plugin directory. Then vim a file and type :help vimspell.

The page on word completion also shows how to load a dictionary. You probably want to put the :set dictionary=/usr/share/dict/words in your .vimrc file. 

_____
### PLUGINS
Checking www.vim.org shows over a thousand downloadable plugins (scripts). Here are some useful ones:

    matchit: extended % matching for HTML, LaTeX, etc...
    vimspell: spell checker
    timestamp: automatically timestamp files



____ 
### EXTRAS
:set rightleft
    :help uganda
    :help!
    :help 42
    :help quotes
    :help holy-grail

https://www.cs.swarthmore.edu/oldhelp/vim/home.html
