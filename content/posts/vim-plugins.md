---
title: "Vim-plugins - which and why?"
date: 2022-02-20T09:27:51+01:00
draft: false
tags: [vim]
categories: [blog]
---

# Vim plugins

Vim is extremely configurable and the internet is full with plug-ins to support
any kind of task. On this page I list the plug-ins that I find useful and
what I use them for. For details see the documentation of the respective
plugins.


# Daily use

## [BlueCatMe/TempKeyword](https://github.com/BlueCatMe/TempKeyword)

Add words under your cursor to a temporary highlight group using ```<Leader>0-9```.


## [andymass/vim-matchup](https://github.com/andymass/vim-matchup)

Smarter matching of opening and closing brackets using ```%```: it also adds programming
related (for instance, linking ```if``` and ```endif```)


## [dense-analysis/ale](https://github.com/dense-analysis/ale)

Asynchronous Lint Engine: run various linters in the background and jump between
issues using vim's location list. (```[l``` and ```]l```).


## [jiskattema/new-moon.vim](https://github.com/jiskattema/new-moon.vim)

My personalized colorscheme, based on new-moon.


## [preservim/tagbar](https://github.com/preservim/tagbar)

Show the tags in the current file in a split window, toggle with
```<Leader>b```.


## [kana/vim-fakeclip](https://github.com/kana/vim-fakeclip)

Link the system's clipboard and ```tmux``` or ```gnuscreen``` paste buffers to
vims registers (```"+``` and ```"&```).


## [natebosch/vim-lsc](https://github.com/natebosch/vim-lsc)

Asynchronously connect to a language server.
Provides omnicompletion and code navigation etc.


## [pbrisbin/vim-mkdir](https://github.com/pbrisbin/vim-mkdir)

Create directories when needed: ```:e new_dir/new_file.txt```.


## [tpope/vim-unimpaired](https://github.com/tpope/vim-unimpaired)

Keymappings to toggle various options and to move around (buffer,
argument, quickfix and location location lists)


## [tpope/vim-vinegar](https://github.com/tpope/vim-vinegar)

Sensible configuration for the default NetRW plug-in.
Press ```-``` to open a file browser.


## [skywind3000/vim-quickui](https://github.com/skywind3000/vim-quickui)

Adds a menu bar (```<Leader><Leader>```) for seldom used commands,
and pop-up buffer selector (```|```).

# Sporadic use

## [brtastic/vim-vorg](https://github.com/jiskattema/vim-vorg)

My clone and personalization of (emacs) org-mode inspired notekeeping.


## [joanrivera/vim-zimwiki-syntax](https://github.com/joanrivera/vim-zimwiki-syntax)

Syntax highlighting for [Zim Wiki](https://zim-wiki.org/) files.


## [mhinz/vim-signify](https://github.com/mhinz/vim-signify)

Show changes to the current file in the sign column.
Uses ```git``` etc. to find changes; jump between changes using ```[c``` and
```]c```.


## [jeetsukumaran/vim-indentwise](https://github.com/jeetsukumaran/vim-indentwise)

Jump through the file using relative indentation depth (```[-```, ```[+```,
```[=``` etc.) or to the begin or end of the current block (```[%``` and
```]%```).


## [jreybert/vimagit](https://github.com/jreybert/vimagit)

Stage and commit changes to git.


## [junegunn/limelight.vim](https://github.com/junegunn/limelight.vim)

Distraction free editting. Only the current paragraph is in focus.


## [michaeljsmith/vim-indent-object](https://github.com/michaeljsmith/vim-indent-object)

Defines a text object ```i``` reflecting the current indentation block.


## [mattn/emmet-vim](https://github.com/mattn/emmet-vim)

Quickly create XML-like files.


## [hrsh7th/vim-vsnip](https://github.com/hrsh7th/vim-vsnip)

Snippet manager. Expand using ```C-l``` in insert mode; jump around using
```Tab```.


## [rafamadriz/friendly-snippets](https://github.com/rafamadriz/friendly-snippets)

A set of snippets.


## [tpope/vim-surround](https://github.com/tpope/vim-surround)

Manipulate characters surrounding objects; fi. change surrounding square brackets into curly brackets:
```cs[}```.


## [tpope/vim-speeddating](https://github.com/tpope/vim-speeddating)

Increment ```C-a``` or decrement ```C-x``` numbers and dates under your cursor.


## [tpope/vim-rsi](https://github.com/tpope/vim-rsi)

Readline key mappings for vim insert mode. Go to begin/end (```C-a```, ```C-e```) and
kill to begin/end (```C-u```, ```C-k```).
Move cursor forward/backward (```C-f```, ```C-b````).


## [tpope/vim-characterize](https://github.com/tpope/vim-characterize)

Enhanced version of ```ga```; shows information on the character under your
cursor.


## [tpope/vim-commentary](https://github.com/tpope/vim-commentary)

Comment-out or un-comment text using ```gc```.


## [tpope/vim-repeat](https://github.com/tpope/vim-repeat)

If installed, other plugins by tpope are repeatable (```.```).


# Still trying out

These plugins seem useful, but in practice I hardly use them.


## [cohama/agit.vim](https://github.com/cohama/agit.vim)

Explore commits and the commit log.


## [junegunn/vim-easy-align](https://github.com/junegunn/vim-easy-align)

Align selection; bound to visual mode ```<Enter>```.


## [kkoomen/vim-doge](https://github.com/kkoomen/vim-doge)

Documentation generator; bound to ```<Leader>d```.


## [sillybun/vim-repl](https://github.com/sillybun/vim-repl)

Read-evaluate-print-loop support using vim's ```:terminal```.
For python, also integrates the debugger.


## [tommcdo/vim-ninja-feet](https://github.com/tommcdo/vim-ninja-feet)

Move to the beginning or end of the current object; mostly useful for things
like delete to the end of the current paragraph (```d]ap```).
