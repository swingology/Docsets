

# FZF CHEATSHEET

## FZF SHELL

### MOST USED
**GENERIC PROTOYPE**

COMMAND [DIRECTORY/] [FUZZY_PATTERN] **<TAB>

<c-r>   
<c-t> 
<c-b>
fzff                    - custom with bat preview
fzf --exact             - exact match
fzf -m                  - multi select mode
CTRL-T                  - paste path fo file 
CTRL-R                  - search COMMAND HISTORY
ALT-C                   - cd to specific directory


**AUTOCOMPLETION**

vim **<TAB>       - open file under current directory
vim ../**<TAB>    - open file under parent directory
vim ~/**<TAB>     - open file under $HOME
cd **<TAB>        - go to a directory under current directory

#### FZF IN NVIM

vim $(fzf)
    <Enter>: open file in current window
    Ctrl + T: open file in new tab page
    Ctrl + X: open file in new horizontal window
    Ctrl + V: open file in new vertical window

You can use Ctrl + N and Ctrl + P or the arrow key to navigate through the list of files found by fzf. To open the file in Neovim, fzf provides several shortcut key:
in multiple searces

nnoremap <silent> <leader>f :FZF<cr>
nnoremap <silent> <leader>F :FZF ~<cr>


************************************************************
-----

**IN SEARCH**
You can select multiple items with TAB key

Press CTRL-Y to copy the line to clipboard and aborts fzf (requires pbcopy)
Press F1 to open the file with less without leaving fzf


#### Search Tips
Does no support regex - such as *.sh
! to negate matching

| Token     | Match type                 | Description                          |
| --------- | -------------------------- | ------------------------------------ |
| `sbtrkt`  | fuzzy-match                | Items that match `sbtrkt`            |
| `'wild`   | exact-match (quoted)       | Items that include `wild`            |
| `^music`  | prefix-exact-match         | Items that start with `music`        |
| `.mp3$`   | suffix-exact-match         | Items that end with `.mp3`           |
| `!fire`   | inverse-exact-match        | Items that do not include `fire`     |
| `!^music` | inverse-prefix-exact-match | Items that do not start with `music` |
| `!.mp3$`  | inverse-suffix-exact-match | Items that do not end with `.mp3`    |




vim -o 'fzf' open a file in vim named fzf 
fzf | xargs ls -l  -  print info for each selected file


#### Fuzzy Completion for shell 
vim ~/paht





### setting default fzf command call
export FZF_DEFAULT_OPTS='--height 40% --layout=reverse --border'

CTRL-T - Paste the selected files and directories onto the command-line
    Set FZF_CTRL_T_COMMAND to override the default command
    Set FZF_CTRL_T_OPTS to pass additional options
CTRL-R - Paste the selected command from history onto the command-line
    If you want to see the commands in chronological order, press CTRL-R again which toggles sorting by relevance
    Set FZF_CTRL_R_OPTS to pass additional options
ALT-C - cd into the selected directory
    Set FZF_ALT_C_COMMAND to override the default command
    Set FZF_ALT_C_OPTS to pass additional options




######################******************************************
## REFERENCE
find * -type f | fzf > selected
 - `CTRL-J` / `CTRL-K` (or `CTRL-N` / `CTRL-P`) to move cursor up and down
 - `Enter` key to select the item, `CTRL-C` / `CTRL-G` / `ESC` to exit
 - On multi-select mode (`-m`), `TAB` and `Shift-TAB` to mark multiple items
 - Emacs style key bindings
 - Mouse: scroll, click, double-click; shift-click and shift-scroll on
   multi-select mode
Layout
vim $(fzf --height 40%)
```shell
vim $(fzf --height 40%)
vim $(fzf --height 40% --reverse)
```
You can add these options to `$FZF_DEFAULT_OPTS` so that they're applied by
default. For example,
```shell
export FZF_DEFAULT_OPTS='--height 40% --layout=reverse --border'
```
| Token     | Match type                 | Description                          |
| --------- | -------------------------- | ------------------------------------ |
| `sbtrkt`  | fuzzy-match                | Items that match `sbtrkt`            |
| `'wild`   | exact-match (quoted)       | Items that include `wild`            |
| `^music`  | prefix-exact-match         | Items that start with `music`        |
| `.mp3$`   | suffix-exact-match         | Items that end with `.mp3`           |
| `!fire`   | inverse-exact-match        | Items that do not include `fire`     |
| `!^music` | inverse-prefix-exact-match | Items that do not start with `music` |
| `!.mp3$`  | inverse-suffix-exact-match | Items that do not end with `.mp3`    |
```
^core go$ | rb$ | py$
```
#### Environment variables
- `FZF_DEFAULT_COMMAND`
  - Default command to use when input is tty
  - e.g. `export FZF_DEFAULT_COMMAND='fd --type f'`
  - > ⚠️ This variable is not used by shell extensions due to the
    > slight difference in requirements.
    >
    > (e.g. `CTRL-T` runs `$FZF_CTRL_T_COMMAND` instead, `vim **<tab>` runs `_fzf_compgen_path()`, and `cd **<tab>` runs `_fzf_compgen_dir()`)
    >
    > The available options are described later in this document.


 - `FZF_DEFAULT_OPTS`



   - Default options

   - e.g. `export FZF_DEFAULT_OPTS="--layout=reverse --inline-info"`

unset **<TAB>
export **<TAB>
unalias **<TAB>




#### FZF with files and Dir
# Files under the current directory
# - You can select multiple items with TAB key
vim **<TAB>

# Files under parent directory
vim ../**<TAB>

# Files under parent directory that match `fzf`
vim ../fzf**<TAB>

# Files under your home directory
vim ~/**<TAB>


# Directories under current directory (single-selection)
cd **<TAB>

# Directories under ~/github that match `fzf`
cd ~/github/fzf**<TAB>
i


#### Process Id
Can select multiple processes with <TAB> or <Shift-TAB> keys
```
kill -9 <TAB>
```


#### Host Names
ssh **<tab>

















 #### [Options](https://github.com/junegunn/fzf#options)
  
https://www.youtube.com/watch?v=gdVjVtpr55M&list=PL-qpqUnq0PzQe6g2bgPzYGcvFwsRAZOU7&index=3&ab_channel=PTXofficial
https://www.youtube.com/watch?v=ghs09zm90Rg
https://www.youtube.com/watch?v=gw2rhd-s8rc&ab_channel=TechVision
https://www.youtube.com/watch?v=i7OE-Ijr2Cs
https://www.youtube.com/watch?v=j4xgkjWlfL4
https://www.youtube.com/watch?v=jEtpKUUxVGQ

https://www.youtube.com/watch?v=k6X_NS_Vkv8
https://www.youtube.com/watch?v=kRkp-uJTK7s
https://www.youtube.com/watch?v=kc0tRPtsdcU&ab_channel=CNBCTelevision
https://www.youtube.com/watch?v=kcoch-Mpgls
https://www.youtube.com/watch?v=kfaVY1VSdFk
https://www.youtube.com/watch?v=lJlEQim-yMo
https://www.youtube.com/watch?v=lZ3bPUKo5zc
https://www.youtube.com/watch?v=ly4S0oi3Yz8&t=3s
https://www.youtube.com/watch?v=mMw2_f0lWx4&ab_channel=DoubleHike
https://www.youtube.com/watch?v=mRD0-GxqHVo&list=RDCLAK5uy_kmPRjHDECIcuVwnKsx2Ng7fyNgFKWNJFs&index=9
https://www.youtube.com/watch?v=mdXgJH8wYik
https://www.youtube.com/watch?v=n9Y2Eb4BaSg
https://www.youtube.com/watch?v=nIJQPX5kxp4&ab_channel=ProfessorLeonardhttps://www.youtube.com/watch?v=njKP3FqW3Sk&t=1s&ab_channel=AlexanderAminihttps://www.youtube.com/watch?v=oBt53YbR9Kkhttps://www.youtube.com/watch?v=oPEBWXvo1Xc&list=RDpkitw9LUB88&index=2&ab_channel=Jacob'sPianohttps://www.youtube.com/watch?v=oXlwWbU8l2ohttps://www.youtube.com/watch?v=p5jRKV2ptBMhttps://www.youtube.com/watch?v=p9gzGmyDJvchttps://www.youtube.com/watch?v=qQ-56b_LvOwhttps://www.youtube.com/watch?v=qbW6FRbaSl0&ab_channel=KalleHalldenhttps://www.youtube.com/watch?v=qew2m1UdbXkhttps://www.youtube.com/watch?v=qgG5Jhi_Elshttps://www.youtube.com/watch?v=rMBrTMfFI6I&ab_channel=MusicLabhttps://www.youtube.com/watch?v=rOLGvZagdC0https://www.youtube.com/watch?v=rPq0Elf18n4https://www.youtube.com/watch?v=rR4n-0KYeKQhttps://www.youtube.com/watch?v=rZufA635dq4&t=1shttps://www.youtube.com/watch?v=rfscVS0vtbwhttps://www.youtube.com/watch?v=sKmTYkGwmN0&ab_channel=NBCNewshttps://www.youtube.com/watch?v=sV1QoLqLYL0https://www.youtube.com/watch?v=sW9npZVpiMIhttps://www.youtube.com/watch?v=sz25xxF_AVEhttps://www.youtube.com/watch?v=tPYj3fFJGjkhttps://www.youtube.com/watch?v=th3zZ4jmviMhttps://www.youtube.com/watch?v=trGEGhitN4Ahttps://www.youtube.com/watch?v=tysPbjturcg&ab_channel=MoonChanelhttps://www.youtube.com/watch?v=u5wtoH0_KuA&ab_channel=TwoMinutePapershttps://www.youtube.com/watch?v=uKGvG9DfDLAhttps://www.youtube.com/watch?v=uPUEq8d73JI&ab_channel=LexFridmanhttps://www.youtube.com/watch?v=vGsOA2eqkighttps://www.youtube.com/watch?v=vT1JzLTH4G4&list=PLC1qU-LWwrF64f4QKQT-Vg5Wr4qEE1Zxk&index=2https://www.youtube.com/watch?v=wczdECcwRw0https://www.youtube.com/watch?v=wyIR9gPXF5ohttps://www.youtube.com/watch?v=xLr0GStrnwQ&ab_channel=CNBChttps://www.youtube.com/watch?v=xeGE26V4WY0https://www.youtube.com/watch?v=xvqsFTUsOmc&ab_channel=PyOhiohttps://www.youtube.com/watch?v=yJg1FX2goCohttps://www.youtube.com/watch?v=yOyaJXpAYZQhttps://www.youtube.com/watch?v=zB_jQ8SUjKEhttps://www.youtube.com/watch?v=zg9ih6SVACc&t=13shttps://www.youtube.com/watch?v=zg9ih6SVACc&t=13s&ab_channel=freeCodeCamp.orghttps://xenovation.com/blog/source-control-management/git/how-to-change-remote-git-repository#list-your-existing-remoteshttps://youtube-vos.org/dataset/vis/https://zealdocs.org/https://zoom.us/https://zoom.us/download?os=linuxhttps://zoomadmin.com/HowToInstall/UbuntuPackage/pm-utilshttps://zsh.sourceforge.io/
426:[https://dev.to/hayden/optimizing-your-workflow-with-fzf-ripgrep-2eai](https://dev.to/hayden/optimizing-your-workflow-with-fzf-ripgrep-2eai)
667:[https://github.com/BurntSushi/ripgrep#installation](https://github.com/BurntSushi/ripgrep#installation)
668:[https://github.com/BurntSushi/ripgrep/blob/master/GUIDE.md](https://github.com/BurntSushi/ripgrep/blob/master/GUIDE.md)
669:[https://github.com/BurntSushi/ripgrep/issues/1190](https://github.com/BurntSushi/rip  3
  4 - `CTRL-J` / `CTRL-K` (or `CTRL-N` / `CTRL-P`) to move cursor up and down
  5 - `Enter` key to select the item, `CTRL-C` / `CTRL-G` / `ESC` to exit
  6 - On multi-select mode (`-m`), `TAB` and `Shift-TAB` to mark multiple items
  7 - Emacs style key bindings
  8 - Mouse: scroll, click, double-click; shift-click and shift-scroll on
  9   multi-select mode
 10
 11 Layout
 12
 13 vim $(fzf --height 40%)
 14
 15 ```shell
 16 vim $(fzf --height 40%)
 17
 18 vim $(fzf --height 40% --reverse)
 19 ```
 20
 21 You can add these options to `$FZF_DEFAULT_OPTS` so that they're applied by
 22 default. For example,
 23
 24 ```shell
 25 export FZF_DEFAULT_OPTS='--height 40% --layout=reverse --border'
 26 ```
 27
 28 | Token     | Match type                 | Description                          |
 29 | --------- | -------------------------- | ------------------------------------ |
 30 | `sbtrkt`  | fuzzy-match                | Items that match `sbtrkt`            |
 31 | `'wild`   | exact-match (quoted)       | Items that include `wild`            |
 32 | `^music`  | prefix-exact-match         | Items that start with `music`        |
 33 | `.mp3$`   | suffix-exact-match         | Items that end with `.mp3`           |
 34 | `!fire`   | inverse-exact-match        | Items that do not include `fire`     |
 35 | `!^music` | inverse-prefix-exact-match | Items that do not start with `music` |
 36 | `!.mp3$`  | inverse-suffix-exact-match | Items that do not end with `.mp3`    |
 37
 38 ```
 39 ^core go$ | rb$ | py$
 40 ```
 41
 42 #### Environment variables
 43
 44 - `FZF_DEFAULT_COMMAND`
 45
 46   - Default command to use when input is tty
 47   - e.g. `export FZF_DEFAULT_COMMAND='fd --type f'`
 48   - > ⚠️ This variable is not used by shell extensions due to the
 49     > slight difference in requirements.
 50     >
 51     > (e.g. `CTRL-T` runs `$FZF_CTRL_T_COMMAND` instead, `vim **<tab>` runs `_fzf_compgen_path()`, and `cd **<tab>` runs `_fzf_compgen_dir()`)
 52     >
 53     > The available options are described later in this document.
 54
 55 - `FZF_DEFAULT_OPTS`
 56
 57   - Default options
 58   - e.g. `export FZF_DEFAULT_OPTS="--layout=reverse --inline-info"`
 59
 60 #### [Options](https://github.com/junegunn/fzf#options)
 61
 62 See the man page (`man fzf`) for the full list of options.
 63
 64 fzf-tmux script
 65
 66 ```shell
 NORMAL  fzf cheatsheet.md                                                                                         markdown  utf-8[dos]  1,427 words  0% :1/338☰ :1  ☲ [46]trailing 
  9   multi-select mode
 10
 11 Layout
 12
 13 vim $(fzf --height 40%)
 14
 15 ```shell
 16 vim $(fzf --height 40%)
 17
 18 vim $(fzf --height 40% --reverse)
 19 ```
 20
 21 You can add these options to `$FZF_DEFAULT_OPTS` so that they're applied by
 22 default. For example,
 23
 24 ```shell
 25 export FZF_DEFAULT_OPTS='--height 40% --layout=reverse --border'
 26 ```
 27
 28 | Token     | Match type                 | Description                          |
 29 | --------- | -------------------------- | ------------------------------------ |
 30 | `sbtrkt`  | fuzzy-match                | Items that match `sbtrkt`            |
 31 | `'wild`   | exact-match (quoted)       | Items that include `wild`            |
 32 | `^music`  | prefix-exact-match         | Items that start with `music`        |
 33 | `.mp3$`   | suffix-exact-match         | Items that end with `.mp3`           |
 34 | `!fire`   | inverse-exact-match        | Items that do not include `fire`     |
 35 | `!^music` | inverse-prefix-exact-match | Items that do not start with `music` |
 36 | `!.mp3$`  | inverse-suffix-exact-match | Items that do not end with `.mp3`    |
 37
 38 ```
 39 ^core go$ | rb$ | py$
 40 ```
 41
 42 #### Environment variables
 43
 44 - `FZF_DEFAULT_COMMAND`
 45
 46   - Default command to use when input is tty
 47   - e.g. `export FZF_DEFAULT_COMMAND='fd --type f'`
 48   - > ⚠️ This variable is not used by shell extensions due to the
 49     > slight difference in requirements.
 50     >
 51     > (e.g. `CTRL-T` runs `$FZF_CTRL_T_COMMAND` instead, `vim **<tab>` runs `_fzf_com    en_path()`, and `cd **<tab>` runs `_fzf_compgen_dir()`)
 52     >
 53     > The available options are described later in this document.
 54
 55 - `FZF_DEFAULT_OPTS`
 56
  0 fzf cheatsheet
  1
  2 find * -type f | fzf > selected
  3
  4 - `CTRL-J` / `CTRL-K` (or `CTRL-N` / `CTRL-P`) to move cursor up and down
  5 - `Enter` key to select the item, `CTRL-C` / `CTRL-G` / `ESC` to exit
  6 - On multi-select mode (`-m`), `TAB` and `Shift-TAB` to mark multiple items
  7 - Emacs style key bindings
  8 - Mouse: scroll, click, double-click; shift-click and shift-scroll on
  9   multi-select mode
 10
 11 Layout
 12
 13 vim $(fzf --height 40%)
 14
 15 ```shell
 16 vim $(fzf --height 40%)
 17
 18 vim $(fzf --height 40% --reverse)
 19 ```
 20
 21 You can add these options to `$FZF_DEFAULT_OPTS` so that they're applied by
 22 default. For example,
 23
 24 ```shell
 25 export FZF_DEFAULT_OPTS='--height 40% --layout=reverse --border'
 26 ```
 27
 28 | Token     | Match type                 | Description                          |
 29 | --------- | -------------------------- | ------------------------------------ |
 30 | `sbtrkt`  | fuzzy-match                | Items that match `sbtrkt`            |
 31 | `'wild`   | exact-match (quoted)       | Items that include `wild`            |
 32 | `^music`  | prefix-exact-match         | Items that start with `music`        |
 33 | `.mp3$`   | suffix-exact-match         | Items that end with `.mp3`           |
 34 | `!fire`   | inverse-exact-match        | Items that do not include `fire`     |
 35 | `!^music` | inverse-prefix-exact-match | Items that do not start with `music` |
 36 | `!.mp3$`  | inverse-suffix-exact-match | Items that do not end with `.mp3`    |
 37
 38 ```
 39 ^core go$ | rb$ | py$
 40 ```
 41
 42 #### Environment variables
 43
 44 - `FZF_DEFAULT_COMMAND`
 45
 46   - Default command to use when input is tty
 47   - e.g. `export FZF_DEFAULT_COMMAND='fd --type f'`
 48   - > ⚠️ This variable is not used by shell extensions due to the
 49     > slight difference in requirements.
 50     >
 51     > (e.g. `CTRL-T` runs `$FZF_CTRL_T_COMMAND` instead, `vim **<tab>` runs `_fzf_com    pgen_path()`, and `cd **<tab>` runs `_fzf_compgen_dir()`)
 52     >
 53     > The available options are described later in this document.
 54
 55 - `FZF_DEFAULT_OPTS`
 56
 57   - Default options
 58   - e.g. `export FZF_DEFAULT_OPTS="--layout=reverse --inline-info"`
 59
 60 #### [Options](https://github.com/junegunn/fzf#options)
 61
 62 See the man page (`man fzf`) for the full list of options.
 63
 64 fzf-tmux script
 65
 NORMAL  <tsheet.md   mar…  utf-8[dos]  1,427 words  0% :1/338☰ :1  ☲ [46]tra… 
 64 fzf cheatsheet
 64
 64 find * -type f | fzf > selected
 64
 64 - `CTRL-J` / `CTRL-K` (or `CTRL-N` / `CTRL-P`) to move cursor up and down
 64 - `Enter` key to select the item, `CTRL-C` / `CTRL-G` / `ESC` to exit
 64 - On multi-select mode (`-m`), `TAB` and `Shift-TAB` to mark multiple items
 64 - Emacs style key bindings
 64 - Mouse: scroll, click, double-click; shift-click and shift-scroll on
 64   multi-select mode
 64
 64 Layout
 64
 64 vim $(fzf --height 40%)
 64
 64 ```shell
 64 vim $(fzf --height 40%)
 64
 64 vim $(fzf --height 40% --reverse)
 64 ```
 64
 64 You can add these options to `$FZF_DEFAULT_OPTS` so that they're applied by
 64 default. For example,
 64
 64 ```shell
 64 export FZF_DEFAULT_OPTS='--height 40% --layout=reverse --border'
 64 ```
 64
 64 | Token     | Match type                 | Description                          |
 64 | --------- | -------------------------- | ------------------------------------ |
 64 | `sbtrkt`  | fuzzy-match                | Items that match `sbtrkt`            |
 64 | `'wild`   | exact-match (quoted)       | Items that include `wild`            |
 64 | `^music`  | prefix-exact-match         | Items that start with `music`        |
 64 | `.mp3$`   | suffix-exact-match         | Items that end with `.mp3`           |
 64 | `!fire`   | inverse-exact-match        | Items that do not include `fire`     |
 64 | `!^music` | inverse-prefix-exact-match | Items that do not start with `music` |
 64 | `!.mp3$`  | inverse-suffix-exact-match | Items that do not end with `.mp3`    |
 64
 64 ```
 64 ^core go$ | rb$ | py$
 64 ```
 64
 64 #### Environment variables
 64
 64 - `FZF_DEFAULT_COMMAND`
 64
 64   - Default command to use when input is tty
 64   - e.g. `export FZF_DEFAULT_COMMAND='fd --type f'`
 64   - > ⚠️ This variable is not used by shell extensions due to the
 64     > slight difference in requirements.
 64     >
 65     >
 65     > The available options are described later in this document.
 65
 65 - `FZF_DEFAULT_OPTS`
 65
 65   - Default options
 65   - e.g. `export FZF_DEFAULT_OPTS="--layout=reverse --inline-info"`
 65
 65 #### [Options](https://github.com/junegunn/fzf#options)
 65
 65 See the man page (`man fzf`) for the full list of options.
 65
 65 fzf-tmux script
 65
 65 ```shell
 65 # usage: fzf-tmux [LAYOUT OPTIONS] [--] [FZF OPTIONS]
 65
 65 # See available options
 65 fzf-tmux --help
 65
 65 # select git branches in horizontal split below (15 lines)
 65 git branch | fzf-tmux -d 15
 65
 65 # select multiple words in vertical split on the left (20% of screen width)
 65 cat /usr/share/dict/words | fzf-tmux -l 20% --multi --reverse
 65 ```
 65
 65 ### key bindings
 65
 65 ```shell
 65 The install script will setup the following key bindings for bash, zsh, and fish.
 65
 65     CTRL-T - Paste the selected files and directories onto the command-line
 65         Set FZF_CTRL_T_COMMAND to override the default command
 65         Set FZF_CTRL_T_OPTS to pass additional options
 65     CTRL-R - Paste the selected command from history onto the command-line
 65         If you want to see the commands in chronological order, press CTRL-R again which toggles sorting by relevance
 65         Set FZF_CTRL_R_OPTS to pass additional options
 65     ALT-C - cd into the selected directory
 65         Set FZF_ALT_C_COMMAND to override the default command
 65         Set FZF_ALT_C_OPTS to pass additional options
 65 ```
 65
 65 Fuzzy completion for bash and zsh
 65
 65 #### [Files and Directories](https://github.com/junegunn/fzf#files-and-directories)
 65
 65 Fuzzy completion for files and directories can be triggered if the word before
 65 the cursor ends with the trigger sequence, which is by default `**`.
 65
 65 ```shell
 65 COMMAND [DIRECTORY/][FUZZY_PATTERN]**<TAB>
 65
 65 # Files under the current directory
 65 # - You can select multiple items with TAB key
 65 vim **<TAB>
 65
 65 # Files under parent directory
 64 # Files under parent directory that match `fzf`
 64 vim ../fzf**<TAB>
 63 vim ~/**<TAB>
 63
 62 cd **<TAB>
 62
 61 ```
 61
 61 #### [](https://github.com/junegunn/fzf#process-ids)Process IDs
 61
 60
 60 ```shell
 60 # Can select multiple processes with <TAB> or <Shift-TAB> keys
 60 kill -9 <TAB>
 60 ```
 60
 60 #### Host names
 59 names are extracted from /etc/hosts and ~/.ssh/config.
 59
 59 ```shell
 59 ssh **<TAB>
 59 telnet **<TAB>
 59 ```
 59
 59 ```shell
 59 telnet **<TAB>
 59 ```
 58
 58 ```shell
 58 unset **<TAB>
 58 export **<TAB>
 58 unalias **<TAB>
 58 ```
 58
 58 ### [](https://github.com/junegunn/fzf#executing-external-programs)Executing external programs
 58
 58 You can set up key bindings for starting external processes without leaving
 58 fzf (`execute`, `execute-silent`).
 58
 58 ```shell
 58 # Press F1 to open the file with less without leaving fzf
 58 # Press CTRL-Y to copy the line to clipboard and aborts fzf (requires pbcopy)
 56 See *KEY BINDINGS* section of the man page for details.
 56
 56 ### [](https://github.com/junegunn/fzf#reloading-the-candidate-list)Reloading the candidate list
 56
 56 By binding `reload` action to a key or an event, you can make fzf dynamically
 56 reload the candidate list. See https://github.com/junegunn/fzf/issues/1750 for
 56 more details.
 56
 57
 57 ```shell
 58 ```
 58
 59
 59 ```shell
 60 ```
 60
 60 #### 3. Interactive ripgrep integration
 60
 61 process will restart with the updated query string denoted by the placeholder
 61 expression `{q}`. Also, note that we used `--disabled` option so that fzf
 61 doesn't perform any secondary filtering.
 61
 61 ```shell
 61 INITIAL_QUERY=""
 61 RG_PREFIX="rg --column --line-number --no-heading --color=always --smart-case "
 62
 62 You can set up key bindings for starting external processes without leaving fzf (execute, execute-silent).
 62
 62 # Press CTRL-Y to copy the line to clipboard and aborts fzf (requires pbcopy)
 62 fzf --bind 'f1:execute(less -f {}),ctrl-y:execute-silent(echo {} | pbcopy)+abort'
 62
 61
  0 fzf cheatsheet
  1
  2 find * -type f | fzf > selected
  3
  4 - `CTRL-J` / `CTRL-K` (or `CTRL-N` / `CTRL-P`) to move cursor up and down
  5 - `Enter` key to select the item, `CTRL-C` / `CTRL-G` / `ESC` to exit
  6 - On multi-select mode (`-m`), `TAB` and `Shift-TAB` to mark multiple items
  7 - Emacs style key bindings
  8 - Mouse: scroll, click, double-click; shift-click and shift-scroll on
  9   multi-select mode
 10
 11 Layout
 12
 13 vim $(fzf --height 40%)
 14
 15 ```shell
 16 vim $(fzf --height 40%)
 17
 18 vim $(fzf --height 40% --reverse)
 19 ```
 20
 21 You can add these options to `$FZF_DEFAULT_OPTS` so that they're applied by
 22 default. For example,
 23
 24 ```shell
 25 export FZF_DEFAULT_OPTS='--height 40% --layout=reverse --border'
 26 ```
 27
 28 | Token     | Match type                 | Description                          |
 29 | --------- | -------------------------- | ------------------------------------ |
 30 | `sbtrkt`  | fuzzy-match                | Items that match `sbtrkt`            |
 31 | `'wild`   | exact-match (quoted)       | Items that include `wild`            |
 32 | `^music`  | prefix-exact-match         | Items that start with `music`        |
 33 | `.mp3$`   | suffix-exact-match         | Items that end with `.mp3`           |
 34 | `!fire`   | inverse-exact-match        | Items that do not include `fire`     |
 35 | `!^music` | inverse-prefix-exact-match | Items that do not start with `music` |
 36 | `!.mp3$`  | inverse-suffix-exact-match | Items that do not end with `.mp3`    |
 37
 38 ```
 39 ^core go$ | rb$ | py$
 40 ```
 41
 42 #### Environment variables
 43
 44 - `FZF_DEFAULT_COMMAND`
 45
 46   - Default command to use when input is tty
 47   - e.g. `export FZF_DEFAULT_COMMAND='fd --type f'`
 48   - > ⚠️ This variable is not used by shell extensions due to the
 49     > slight difference in requirements.
 50     >
 51     > (e.g. `CTRL-T` runs `$FZF_CTRL_T_COMMAND` instead, `vim **<tab>` runs `_fzf_compgen_path()`, and `cd **<tab>` runs `_fz    f_compgen_dir()`)
 52     >
 53     > The available options are described later in this document.
 54
 55 - `FZF_DEFAULT_OPTS`
 56
 57   - Default options
 58   - e.g. `export FZF_DEFAULT_OPTS="--layout=reverse --inline-info"`
 59
 60 #### [Options](https://github.com/junegunn/fzf#options)
 61
 62 See the man page (`man fzf`) for the full list of options.
 63
 64 fzf-tmux script
 65
 V-LINE  fzf cheatsheet.md                               markdown  utf-8[dos]  2 words  0% :1/338☰ :1  ☲ [283]trailing 
-- VISUAL LINE --
 65
 64 ```shell
 63 $ yes | head -10 | awk '{ print NR, NR % 2 == 0 ? "even" : "odd" }'
 62
 61 1 odd2 even3 odd4 even5 odd6 even7 odd8 even9 odd10 even
 60 ```
 59
 58 u`s`e ^ a`n`d $ to match the start and end of the string respectively, and u`s`e ! to negate matching.
 57
 56 ```shell
 55 # Open file in a Vim
 54 vim -o `fzf`
 53
 52
 51 # Print info for each selected file
 50 fzf | xargs ls -l
 49
 48 # ** fzf completion
 47 vim ~/.dotfiles/**
 46 >
 45
 44
 43
 42 chagning di
 41 cd **
 40
 39
 38 alt c | fzf change dir
 37 ctrl r | fzf command history
 36 ctrl t
 35 ```
 34
 33 ## fzf-tmux
 32
 31 ### Settings
 30
 29 ```shell
 28 # Shows on the right 50%
 27 fzf-tmux -r
 26
 25
 24 # On the left 30%
 23 fzf-tmux -130%
 22
 21 # above cursor
 20 fzf-tmux -u30%
 19
 18 # in pop up window - 50% of screen default
 17 fzf-tmux -p
 16 # 80% width, 60% height
 15 fzf-tmux -p 80%,60%
 14 ```
 13
 12 [fzf/ADVANCED.md at master · junegunn/fzf · GitHub](https://github.com/junegunn/fzf/blob/master/ADVANCED.md#using-fzf-as-the-    secondary-filter)
 11
 10 ### fzf ripgrep integration
  9
  8 Types:
  7
  6 Using fzf as secondary filter
  5
  4 Ripgrep then fzf
  3
  2 serach for a line, preview in bat, then search for more files with new searches
  1
  0 USsing fzf as interacgive ripgrep launcher
 V-LINE  fzf cheatsheet.md                       markdown  utf-8[dos]  1,427 words  100% :338/338☰ :1  ☲ [283]trailing 
-- VISUAL LINE --
 58
 59
 59 ```shell
 60 ```
 60
 60 #### [](https://github.com/junegunn/fzf#3-interactive-ripgrep-integration)3. Interactive ripgrep integration
 60
 61 process will restart with the updated query string denoted by the placeholder
 61 expression `{q}`. Also, note that we used `--disabled` option so that fzf
 61 doesn't perform any secondary filtering.
 61
 61 ```shell
 61 INITIAL_QUERY=""
 61 RG_PREFIX="rg --column --line-number --no-heading --color=always --smart-case "
 62
 62 You can set up key bindings for starting external processes without leaving fzf (execute, execute-silent).
 62
 62 # Press F1 to open the file with less without leaving fzf
 62 # Press CTRL-Y to copy the line to clipboard and aborts fzf (requires pbcopy)
 62 fzf --bind 'f1:execute(less -f {}),ctrl-y:execute-silent(echo {} | pbcopy)+abort'
 62
 61
 62 1. Update the list of processes by pressing CTRL-R
 62
 62 FZF_DEFAULT_COMMAND='ps -ef' \
 62   fzf --bind 'ctrl-r:reload($FZF_DEFAULT_COMMAND)' \
 62       --header 'Press CTRL-R to reload' --header-lines=1 \
 62       --height=50% --layout=reverse
 62
 62 2. Switch between sources by pressing CTRL-D or CTRL-F
 62
 62 FZF_DEFAULT_COMMAND='find . -type f' \
 62   fzf --bind 'ctrl-d:reload(find . -type d),ctrl-f:reload($FZF_DEFAULT_COMMAND)' \
 62       --height=50% --layout=reverse
 62
 62 3. Interactive ripgrep integration
 62
 64
 64 INITIAL_QUERY=""
 64 RG_PREFIX="rg --column --line-number --no-heading --color=always --smart-case "
 64 FZF_DEFAULT_COMMAND="$RG_PREFIX '$INITIAL_QUERY'" \
 64   fzf --bind "change:reload:$RG_PREFIX {q} || true" \
 64       --ansi --disabled --query "$INITIAL_QUERY" \
 64       --height=50% --layout=reverse
 64 ```
 64
 64 ## PREVIEW
 64
 64 ```
 64 # {} is replaced with the single-quoted string of the focused line
 64 fzf --preview 'cat {}
 64
 64 fzf --preview 'bat --style=numbers --color=always --line-range :500 {}'
 64
 64 fzf --height 40% --layout reverse --info inline --border \
 64     --preview 'file {}' --preview-window up,1,border-horizontal \
 64     --color 'fg:#bbccdd,fg+:#ddeeff,bg:#334455,preview-bg:#223344,border:#778899'
 64 ''
 64 ```
 64
 64 ## TIPS
 64
 64 ```shell
 64 # Feed the output of fd into fzf
 64 fd --type f | fzf
 64
 64 # Setting fd as the default source for fzf
 64 export FZF_DEFAULT_COMMAND='fd --type f'
 64
 63
 63 # To apply the command to CTRL-T as well
 63 export FZF_CTRL_T_COMMAND="$FZF_DEFAULT_COMMAND"
 63
 63
 63 #If you want the command to follow symbolic links and don't want it to exclude hidden files, use the following command:
 63 export FZF_DEFAULT_COMMAND='fd --type f --hidden --follow --exclude .git'
 63 ```
 63
 63 FREECODECAMP FZF
 64
 64 fzf --height 40% --layout reverse --info inline --border \
 64     --preview 'file {}' --preview-window up,1,border-horizontal \
 64     --color 'fg:#bbccdd,fg+:#ddeeff,bg:#334455,preview-bg:#223344,border:#778899'
 64 ''
 64 ```
 64
 64 ## TIPS
 64
 64 ```shell
 64 # Feed the output of fd into fzf
 64 fd --type f | fzf
 64
 64 # Setting fd as the default source for fzf
 64 export FZF_DEFAULT_COMMAND='fd --type f'
 64
 63
 63 # To apply the command to CTRL-T as well
 63 export FZF_CTRL_T_COMMAND="$FZF_DEFAULT_COMMAND"
 63
 63
 63 #If you want the command to follow symbolic links and don't want it to exclude hidden files, use the following command:
 63 export FZF_DEFAULT_COMMAND='fd --type f --hidden --follow --exclude .git'
 63 ```
 63
 63 FREECODECAMP FZF
  1
  0 3. Interactive ripgrep integration
  1
  2 The following example uses fzf as the selector interface for ripgrep. We bound reload action to change event, so every time y    ou type on fzf, the ripgrep process will restart with the updated query string denoted by the placeholder expression {q}. Als    o, note that we used --disabled option so that fzf doesn't perform any secondary filtering.
  3
  4 INITIAL_QUERY=""
  5 RG_PREFIX="rg --column --line-number --no-heading --color=always --smart-case "
  6 FZF_DEFAULT_COMMAND="$RG_PREFIX '$INITIAL_QUERY'" \
  7   fzf --bind "change:reload:$RG_PREFIX {q} || true" \
  8       --ansi --disabled --query "$INITIAL_QUERY" \
  9       --height=50% --layout=reverse
 10 ```
 11
 12 ## PREVIEW
 13
 14 ```
 15 # {} is replaced with the single-quoted string of the focused line
 16 fzf --preview 'cat {}
 17
 18 fzf --preview 'bat --style=numbers --color=always --line-range :500 {}'
 19
 20 fzf --height 40% --layout reverse --info inline --border \
 21     --preview 'file {}' --preview-window up,1,border-horizontal \
 22     --color 'fg:#bbccdd,fg+:#ddeeff,bg:#334455,preview-bg:#223344,border:#778899'
 23 ''
 24 ```
 25
 26 ## TIPS
 27
 28 ```shell
 29 # Feed the output of fd into fzf
 30 fd --type f | fzf
 31
 32 # Setting fd as the default source for fzf
 33 export FZF_DEFAULT_COMMAND='fd --type f'
 34
 35 # Now fzf (w/o pipe) will use fd instead of find
 36 fzf
 37
 38 # To apply the command to CTRL-T as well
 39 export FZF_CTRL_T_COMMAND="$FZF_DEFAULT_COMMAND"
 40
 41
 42 #If you want the command to follow symbolic links and don't want it to exclude hidden files, use the following command:
 43 export FZF_DEFAULT_COMMAND='fd --type f --hidden --follow --exclude .git'
 44 ```
 45
 46 FREECODECAMP FZF
 47 Why you should be using fzf, the command line fuzzy finder
 48
 49 ```shell
 50 $ yes | head -10 | awk '{ print NR, NR % 2 == 0 ? "even" : "odd" }'
 51
 52 1 odd2 even3 odd4 even5 odd6 even7 odd8 even9 odd10 even
 53 ```
 54
 55 u`s`e ^ a`n`d $ to match the start and end of the string respectively, and u`s`e ! to negate matching.
 56
 57 ```shell
 58 # Open file in a Vim
 59 vim -o `fzf`
 60
 61
 62 # Print info for each selected file
 NORMAL  fzf cheatsheet.md                        markdown  utf-8[dos]  1,427 words  66% :225/338☰ :1  ☲ [283]trailing 
