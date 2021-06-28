# VISUAL STUDIO CODE CHEATSHEET

| Shortcut | action| Default | Mac | Linux |
|-----| -----| -----| ----| -----|
| <C-Shift> + up/down | multir cursor - <esc> <esc> to clear| X |x | |
| <C-tab> | cycle tabs in window | x |x | | 
| <cmd - b> | toggl sidebar | x | x |  |
| <cmd-shift - e> | toggle file explorer | x | x | |
| <c-r> | switching workspaces | x | x | |              @FIXME: @CONFLICT:
| <cmd-`>| toggle terminal | x | x | |
|<cmd-p>| goto a file | x | x| |
|<c-g> | gott a line | x | x | |
| <cmd-opt-#>| create a split| x | x | |
| <cmd - k><s-enter> | 

Toggle editor group layout

You can also toggle between horizontal or vertical split layouts in VS Code. To do so, you use the toggle editor group command.

The original keyboard shortcut is command + option + 0. I switched it to command + option + 1.

Working with tabs

You can open a new tab by hitting command + t.

To switch between tabs, you use command + the tab number. 1 works for the leftmost tab; 2 for the second tab, and so on.

If you want to switch between tabs in different editors, use ctrl + the editor number. 1 works for the leftmost editor; 2 works for the second editor, and so on.

To close a tab, use command + w.
Select word

To select a word, use command + d. If you hit command + d more than once, you’ll add another occurrence of the same keyword to your selection.

To select all instances of a keyword in the same file, use ctrl + command + g. You can also use command + F2.
Folding and unfolding

To fold code, use command + opt + [. This command lets you hide code that you might not need.

To unfold code, use command + opt + ]
Move line upwards or downwards.

To move a line upwards or downwards, use opt + the up or down arrow key.
Split lines

To split a selection into multiple lines, first select multiple lines, then use command + opt + l.
Pageup / Pagedown

If you want to move up or down a document quickly, like through the good old pageup or pagedown shortcut in Windows, you can use fn + up or fn + down.
Jump to word

To jump to a word in VS Code, you need to install the Jumpy extension.

Once you’ve installed Jumpy, you can activate Jumpy’s “word mode” through the command line to enter the word jump mode.

In this mode, you can type the two letter characters that’s shown all over the editor to jump to the right word.

To exit jumpy’s word mode, you can type a non a-z character like space or enter.
i
I set the Jumpy’s word mode keyboard shortcut to command + j since J stands for jump.
Expand Region

The Expand region shortcut can only be used if you have installed the Expand Region extension. It should have been in the last video, but I completely forgot about it.

Expand region lets you select a word, expand the selection upwards to the containing brackets (or tags), then another level of brackets, and so on.

To expand upwards, I set the keyboard shortcut to command + option + up.

To undo the expansion, I set the keyboard shortcut to command + option + down.

[source](https://zellwk.com/blog/useful-vscode-keyboard-shortcuts/)

## VSC Vim KeyBindings
| Shortcut | action| mode| Default | Mac | Linux | VIM |
|-----| -----| -----|----| -----| ----| --- |
| hjkl | moving | nv| x | | | x |
| i | insert mode |nv| x | | | x |
| <esc> or <C-c> | normal mode | iv | x | | | x |
| |
| **GENERAL NAVI - in file**|
| w / b | jump to start of word forward / back | nv | x| | | x |
| e / ge | jump to end of word forward / back | nv | x| | | x |
| W/B/E/GE | jump to connected full connected word | nv | x | | | x |
| |
| **MOVING IN A LINE** |
| 0 | move to first char of line | nv | x | | | x |
| $ | move to last char of line | nv | x | | | x |
| ^ | move to first non blank char of line | nv | x | | | x |
| g_ | move to last non blank char of line | nv | x | | | x |
| |
| **LARGE MOVES**|
| { } | jump paragraph up / down | nv | x | | | x |
| <C-d> | jump half page down | nv | x | | | |
| <C-u> | jump half page up | nv | x | | | |
| |
| **SEARCHING** |
| f{char} / F{char} | move to next / prior occurence of {char} | nv | x | ||| |
| ; / , | ***continue*** - repeat last {char} search | nv | x | | | | |
|/{pattern}| forward {pattern} search | nv | x |||x |
|?{pattern}| back {pattern} search | nv | x | | | x |
| <CR> | after search to jump to result | nv | x | | | x |
| n / N | forward and back during search | nv | x | | | x |
| |
| **MOVING WITH COUNTS** |
| {count}motion| 2w/2b - moves 2 words - 2j/2k moves 2 lines | nv | x |||x|
||
| **Move Shortcuts** |
| gg / G | top or bottom of line | nv | x | ||x|
| {line}gg | 3gg - go to line 3| nv | x | | | x|
| % | jump to matchin brackets ({[]}) | x | | |x |
||
|**ACTIONS**|
| {operator}{count}{motion} | |||||
|d5j | delete 5 lines down | |||||
| df' | delete to the first ' found including '| |||||
|dt' | delete to the first ' but leave the ' |||||||
| d/hello | delete until 'hello' | ||||||
| gggdG | delete entire document | ||||||
| **operators**| 
| c change| cc change entire line | |||||
| d cut | dd deletes entire line | |||||
|y yank | | |||||
| p paste | | |||||
| g~ toggle caps |  | |||||





@TODO:
The way that you specify a text object within a command is by combining the letter a (which represents the text object plus whitespace) or i (inner object without whitespace) with a character that represents a text object itself: w for word, s for sentence, ' " for quotes, p for paragraph, b for block surrounded by (, Bfor block surrounded by { and t for tag. So to delete different bits of text you could:

    daw to delete a word (plus trailing whitespace)
    ciw to change inner word
    das to delete a sentence (dis delete inner sentence)
    da" to delete something in double quotes including the quotes
    ci" to change something inside double quotes
    dap to delete a paragraph
    dab da( or da) to delete a block surrounded by (
    daB da{ or da} to delete a block surrounded by {
    dat to delete an HTML tag
    cit to change the contents of an HTML tag

Combining text objects with operators is extremely powerful and you’ll use them very often. Stuff like cit, ci" and cib is just brilliant.

Let’s say that we want to change the contents of this string below for something else:

const salute = 'I salute you oh Mighty Warrior'

You type ci'Hi!<ESC> and it becomes:

const salute = 'Hi!'

Just like that. You don’t need to go grab the mouse, select the text and then write something else. You type three letters and Boom.
Noticed How Most Vim Keys Are Placed Near Your Fingers?

The fact that Vim has modes allows keys near the home row to be reused in each separate mode, minimizing the need for slow and contorted key combinations, and heightening your speed and the longevity of your fingers and wrists. This is awesome!
Repeating The Last Change with The Dot Operator

Vim has yet another trick in store for you aimed at saving you more keystrokes: The magic . command. The . command allows you to repeat the last change you made. Imagine that you run dd to delete a line. You could type dd again to delete another line but you could also use . which is just a single keystroke. Ok, you save one keystroke, so what? Well, you can use the . command to repeat any type of change, not just single commands. For instance, you could change a word for “Awesome” like so cawAwesome<CR>, and then repeat that whole command with all those keystrokes by just using .. Think of the possibilities!

The . command works great in combination with the repeat search commands (;, ,, n or N). Imagine that you want to delete all occurrences of cucumber. An alternative3 would be to search for cucumber /cucumber then delete it with daw. From then on you can use n to go to the next match and . to delete it! Two keystrokes!?! Again think of the possibilities!!
Vim’s Secret Language

As you probably have noticed all these operators, counts and motions make up a (programming) language of sorts. You can think of operators as functions and counts and motions as arguments, or using an even simpler analogy… you can think of operators as verbs, counts as adjetives and motions as objects.

The true magic of Vim is composition. As you go building up this vocabulary of operators and motions you’ll find that you can combine them to your heart’s content. So that, once you know all the c, cl, caw, ciw, ct. from the previous paragraph and you learn how dl works, you’ll not only be able to use dl, you’ll know that you can also combine it with all the motions you already have at your disposal and daw, diw, dt, etc.

This is very cool. When using Vim you’ll feel you are navigating a meta-universe of text editing, it’s like programming or controlling the very mechanism of editing and writing text. If you’re familiar with git and how it feels to use the git command line to work with source control, you can think of Vim as the git of text editing. (Putting aside the fact that Vim predates git by almost 30 years). With Vim, you’ll look at a piece of text and you’ll no longer see just words or text, you’ll see the possibilities of an infinite number of operators and motions being applied.
Inserting Text a la Vim

Sooner or later you will have to write some code. In Vim, you write code in Insert mode. You’ve seen a little bit of insert mode when using the c command but let’s look at it some more. There’s two core commands that put you into insert mode: i for insert and a for append.

The i insert command puts you in insert mode before the cursor. While the a append command puts you in insert mode after the cursor (as if to append stuff wherever the cursor is placed). From then on you’re in insert mode and Vim pretty much behaves like any other editor (welcome back VSCode!).

Like with many other Vim commands i and a have uppercase counterparts that do stronger versions of insert and appending. I puts you in insert mode at the beginning of the current line whilst A puts you in insert mode at the end.

In addition to i and a there are another three super useful commands that I love to use to drop into insert mode:

    o inserts a new line below the current one and drops you into insert mode (mnemonic open a line below)
    O inserts a new line above the current one and also drops you into insert mode
    gi puts you into insert mode at the last place you left insert mode. This is great if you drop of insert mode by mistake and want to go back where you were and continue typing.

Ok, so let’s say that now you are in insert mode, typing away and you make a mistake, like a typo. Do you go back to normal mode, fix the typo and go back into insert mode? No! There’s a couple of bindings that can help you fix an error right from within insert mode:

    C-h lets you delete the last character you typed
    C-w lets you delete the last word you typed
    C-u lets you delete the last line you typed

Eventually though you’ll want to exit insert mode and do other stuff. There are three ways to do it: <ESC>, C-[ and C-C. Of all of this, the easier to type is C-C.
Selecting Text in Visual Mode

Visual Mode is the Vim equivalent to selecting text with a mouse. Instead of a mouse though, you’ll use Vim motions. This mode can come very handy whenever you need to select some text because it gives you visual feedback as you do it.

There’s three ways in which you can start visual mode:

    v for visual mode character-wise. When you move around you go selecting character by character
    V for visual mode line-wise. When you move around you go selecting line by line
    <C-V> for visual mode block-wise. When you move around yo go selecting rectangular blocks of text

The visual mode can be very helpful for copying and pasting stuff and when operating on blocks of text or code. It works in the opposite way of normal mode:

    In normal mode you first define the operator and then a motion that represents some text to which to apply that operator
    In visual mode you select the text first and then you type the operator

Splits, Tabs and Switching Between Them

A great feature in Vim is its great support for splits and tabs. Creating, resizing, rearranging and moving between splits and tabs is incredibly easy and fast in Vim. VSCodeVim offers an OK support for this Vim feature.
Splits

Splits are awesome. They allow you to divide your workspace into vertical and horizontal split windows:

    Use the :sp {nameoffile} command to open a horizontal split
    Use the :vsp {nameoffile} command to open a vertical split

You can move between them with <C-W> + hjkl.
Splits in Vim
Typing a Command

Notice the : before some of these commands? The colon triggers command-line mode and sets you up to enter a command (also known as Ex command, you'll find out why later in the book when we dive into command-line mode).

To type an ex command you literally type `:` followed by the name of the command (e.g. :vsp). When you type a colon and a command, the command will be displayed in the lower-left part of the screen.
Tabs

    Use :tabnew {file} to open a file in a new tab
    Use :tabn to go to the next tab
    Use :tabp to go to the previous tab

Surrounding Things With Vim Surround

VsCodeVim comes with a bunch of useful Vim plugins built-in. One of them is vim-surround which extends Vim’s secret language with a new operator: The surround operator or s.

Using this operator we can surround swaths of text using it as you would any other operator within Vim:

    ds' to delete the surrounding ' (ds{char})
    cs'" to change the surrounding ' for " (cs{old}{new})
    ysaptli> to surround a paragraph with an <li> tag (ys{motion}{char})

You can also use vim-surround by selecting a bit of text in visual mode and then using S{desired character}
Moving Even Faster with vim-sneak and vim-EasyMotion

Vim-sneak and vim-EasyMotion are a couple of Vim plugins that overcharge how you move in Vim. Both of these plugins need to be enabled via your VSCodeVim preferences.

Vim-sneak is a middle ground between character search (inside a line) and pattern search (inside a file):

    You type s{char}{char} and the cursor flies to the first occurrence of that two character sequence. From then on type ; for the next occurrence , , for the previous one. The S{char}{char} works in a similar fashion but backwards.

Where vim-surround extended Vim’s secret language with an operator, vim-sneak does the same but with a motion. As such you can use it in combination with other operators:

    Type {operator}z{char}{char} and the operator will be applied over the text traversed by the sneak motion.

Vim-EasyMotion is a weird one as Vim plugins go. It completely bypasses Vim motions and reinvents them in a curious and mindblowing way. When you trigger an easy motion motion it labels the possible targets in the whole document with a key combination that is shown in an overlay (over the text in question). Type that combination and you’re teleported to that location.

For instance, type \\w (the \\ is how you trigger EasyMotion) and EasyMotion will label the beginning of all words ahead of you. Type \\f' and EasyMotion will label all occurrences of the ' character. Pretty nifty, isn’t it?
Vim-Easymotion labeling motions
![iamge](https://www.barbarianmeetscoding.com/images/vscodevim-easymotion.jpg)

Some handy Visual Studio Code only key mappings:

These are some handy mappings the VSCodeVim team came up with only for VSCode:

    gb adds another cursor on the next word it finds which is the same as the word under the cursor. Like * but instead of jumping to next ocurrence it creates multiple cursors.
    af is a visual moe command that selects increasingly larger blocks of text.
    gh is the equivalent of hovering the mouse over where the cursor is. Super handy in order to enable a keyboard only workflow and still enjoy some features (error messages, types, etc) only available via the mouse.

Where Should I Go From Here?

Awesome! We’ve covered a lot of ground in this article and I hope you’ll find it useful as a guide to Vim in Visual Studio Code. All that remains is for you to practice little by little until you become more and more comfortable and proficient with Vim. Don’t try to apply everything you’ve learned in this article at once. Just pick some of the operators you find more useful and slowly go adding them to your workflow.

Even though we covered a lot of ground there’s tons of things we didn’t get to talk about:

    I wrote a complete book that guides you through learning Vim in Visual Studio Code step by step in a lot more depth than this article. It’s free to read online. That’s a great place to continue your Vim in VSCode journey and to use as reference whenever you need it.
    Learn Vim is a VSCode extension I created that helps you learn Vim right within VSCode, keeps your progress and provides room for thoughtful reading and deliberate practice.
    There’s even more plugins available in VSCodeVim. Take a look and see if there’s anything you find interesting
    One of Vim’s core features is its amazing customizability. VSCodeVim brings support for some of that with custom key mappings. That is, it allows you to define custom mappings to make frequent actions easier to type. Take a look here for some great examples.
    Consider installing Neovim and enabling it in VSCode. It allows for an awesome command line mode support. Yep, yet another Vim mode that is capable of some amazing stuff.
    Here is a complete list of the features available right now in VsCodeVim. Yep. It is humongous. Lots of goodies yet to explore.

Go, enjoy your newfound knowledge, improve your skills and productivity and if you ever want to learn more about Vim, I have more awesome stuff for you:

    Try the Exploring Vim series for more involved articles about Vim
    Or the 5 Minutes Vim series for shortish condensed articles
    Or even better get Wizards Use Vim my beautiful book on all things Vim where I guide you step and step in how to be more awesome with Vim


[SOURCE](https://www.barbarianmeetscoding.com/blog/boost-your-coding-fu-with-vscode-and-vim)