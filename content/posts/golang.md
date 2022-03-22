---
title: "Go"
date: 2022-02-17T11:43:06+01:00
tags: ['go']
draft: false
---

To keep my technical skills up-to-date, I decided to have a look at a 'new'
programming language.
My usual toolkit consists of Fortran and C for high-perfomance and scientific
computing. Python for machine learning, some hobbying, and scripting.
Bash for even more scripting.
And Javascript for some web hacking.
Altough I got tired of learning a new web framework every week and gave up on the web completely.
I've played around a bit with CUDA, Ruby, D, C++, Lua, and I'm probably forgetting
some, but I wouldn't call myself an expert in those.
I am also interested in using the language professionally, so the new language
should not be too obscure. (For something exotic, see my page on the elvish
shell).

What I'm looking for is something simpler than C++ and Python: easy syntax,
enough high-level features and a standard library that you don't have to
implement everything yourself, but with good performance.
At least better performance than Python.
When looking at the popular options, Go and Rust, I decided to go for Go.
Rust, whatever else you might think about it, is quite complex.
Although Go's performance probably means it wont replace fortran and C, it could
replace many scripting and Python use.
And it could be that the much hyped concurrency of Go, combined with the gradual performance improvements
Go has been making, make it fast enough to replace even some C and Fortran codes.
So, let's go!

I'll update this page every now and then when I learn something new.

# Install

## Packages

## Virtual environment

## Using a specific Go version

# Write code

## Project layout

## Highlighting

I'm using vim's default Go syntax highlighting.

## Linting

Vim ALE supports several linters (check with ```:ALEInfo```), including ```gofmt```
and ```golint```.
You can run any of those using ```:ALEFix <tool>```.

## Language server

Install with:
```bash
go get golang.org/x/tools/gopls@latest
```

## Logging

## Debugging

## Testing

## Packaging

# Interactive use

## Notebooks 

## REPL

# Recommended packages

