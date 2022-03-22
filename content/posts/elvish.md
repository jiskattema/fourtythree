---
title: "Elvish"
date: 2022-03-05T11:01:42+01:00
draft: false
---

[Elvish](https://elv.sh/) is an (not POSIX compattible) shell, ie. an
alternative to bash etc.
Its main attraction is a clean and readable syntax, and a closer integration
with structural data, JSON.

It also integrates several popular shell extensions in several modes.
(Actually, it provides its own implementation).

[Autojump](https://github.com/wting/autojump) is a way quickly navigate recently
and frequently used directories.
This is implemented in the ```Location mode``` or ```Ctrl-L```.

[FZF](https://github.com/junegunn/fzf) provides interactive fuzzy search for
history and completion. This is used for various modes.

[ranger](https://github.com/ranger/ranger) is a file manager, directory browser.
This is implemented as a file and directory picker in ```Navigation mode``` or
```Ctrl-N```.

# Install

There are fedora packages, but the language is still being updated frequently; best install from git.

## Packages

There is the [elvish package manager - epm](https://elv.sh/ref/epm.html).
But I am not using any packages, except for the built-in ones, for now.

# Write code

## Highlighting

Highlighting for vim is provided by [dmix/elvish.vim](https://github.com/dmix/elvish.vim)

## Language server

The elvish shell executable can also be run as a language server:

```elvish
elvish -lsp
```

## Packaging

This being a scripting langauge, small scripts (with the ```.elv``` extension)
can be run without installation.

Elvish plugins directly extending the language are written in Go,
and follow the Go packaging guidelines.

# Interactive use

## Configuration - rc.elv

Use a smallish part of the screen for completion and history
```elvish
set edit:max-height = 10
```

Hide the righthand prompt
```elvish
set edit:rprompt = (constantly '')
```

Use the external ls command with colors
```elvish
fn ls {|@a| e:ls --color $@a }
```

Smart-case and subsequence matching
```
fn match {|seed|
    var inputs = [(all)]
    var results = []
    for matcher [$edit:match-prefix~ $edit:match-substr~ $edit:match-subseq~] {
        set results = [(put $@inputs | $matcher &smart-case $seed)]
        if (or $@results) {
            put $@results
            return
        }
    }
    put $@results
}

set edit:completion:matcher[''] = $match~
```


## Keybindings

Insert mode : use readline like keybindings
```elvish
use readline-binding
set edit:insert:binding[Ctrl-l] = $edit:clear~
set edit:insert:binding[Ctrl-/] = $edit:location:start~
set edit:insert:binding[Ctrl-n] = $edit:navigation:start~
set edit:insert:binding['Ctrl-['] = $edit:command:start~
```

Command mode : a minimal vi-like normal mode started by pressing escape in
insert mode
```elvish
set edit:command:binding['Enter'] = $edit:smart-enter~
set edit:command:binding[a] = { $edit:move-dot-right~ ; $edit:close-mode~ }
set edit:command:binding[A] = { $edit:move-dot-eol~ ; $edit:close-mode~ }
```

Completion mode : started by tab in insert mode
```elvish
set edit:completion:binding = ( $edit:binding-table~ [
  &Ctrl-p=$edit:completion:up~
  &Ctrl-n=$edit:completion:down~
  &Ctrl-h=$edit:completion:left~
  &Ctrl-l=$edit:completion:right~
  &Tab=   $edit:completion:right~
  &S-Tab= $edit:completion:left~
  &' '=   $edit:completion:accept~
  &Enter= $edit:completion:accept~
])
```

Navigation mode : press Ctrl-n
```elvish
set edit:navigation:binding[Enter]  = $edit:navigation:insert-selected-and-quit~
set edit:navigation:binding[Ctrl-k]  = $edit:navigation:insert-selected~
set edit:navigation:binding[Ctrl-h] = $edit:navigation:left~
set edit:navigation:binding[Ctrl-l] = $edit:navigation:right~
```

History mode : press Ctrl-r
```elvish
set edit:history:binding[Ctrl-n] = $edit:history:down~  # dont enter navigation mode from history
```

Previous command mode : press Alt-,

# Issues - vim

Being not POSIX compliant, vim and its plugins do break at some points.

The first issue I ran into was that elvish requires a space before the output
redirection (ie. ```./program > output.txt```), and Bash doesnt.
For vim and netrw, this can be fixed by setting the shell redirection variable
(note the space at the end):

```vim
set shellredir=\ \>\ 
```

However, more plugins break in unexpected ways.
Some careful reading of the documentation offers an easy way out:

```vim
set shell=/usr/bin/sh
nmap <C-z> :terminal /home/jiska/go/bin/elvish<CR>
```
just have vim use a POSIX compliant shell by default, and explicitly use elvish
when opening an interactive terminal.

# Issues - elvish

## Theming

At the moment, there is no way to set the colors for the user interface and
messages. 
On the dark colorscheme the messages are unreadable.
As a work-around, I hardcoded better colors in the elvish runtime.

## History

There is nothing similar to the bash ```history``` command to write the shell's
history to a file.

UPDATE: I found the ```$edit:command-history~``` builtin function.

## Completion

Tab completion is not perfect yet; tilde expansion prevents automatic selection of single-match
completions and starts the completion mode, instead of immediately completing.

UPDATE: [carapace](https://github.com/rsteube/carapace-bin) provides completion
for many commands, distilled from manpages.
It has different issues though: it breaks filename completion.

# To do

As a shell, I'm quite happy with the status so far.
I have not used it much yet as a scripting and programming language.
If I start _programming_ in elvish, I would like to fix:

 * Linting
 * Logging
 * Debugging
 * Testing
 * Profiling
