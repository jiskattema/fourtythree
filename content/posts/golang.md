---
title: "Go"
date: 2022-02-17T11:43:06+01:00
tags: ['go']
draft: false
---

To keep my technical skills up-to-date, I decided to have a look at a 'new'
programming language.  My usual toolkit consists of Fortran and C for
high-perfomance and scientific computing. Python for machine learning, some
hobbying, and scripting.  Bash for even more scripting.  And Javascript for some
web hacking.  Altough I got tired of learning a new web framework every week and
gave up on the web completely.  I've played around a bit with CUDA, Ruby, D,
C++, Lua, and I'm probably forgetting some, but I wouldn't call myself an expert
in those.  I am also interested in using the language professionally, so the new
language should not be too obscure. (For something exotic, see my page on the
elvish shell).

What I'm looking for is something simpler than C++ and Python: easy syntax,
enough high-level features and a standard library that you don't have to
implement everything yourself, but with good performance.  At least better
performance than Python.  When looking at the popular options, Go and Rust, I
decided to go for Go.  Rust, whatever else you might think about it, is quite
complex.  Although Go's performance probably means it wont replace fortran and
C, it could replace many scripting and Python use.  And it could be that the
much hyped concurrency of Go, combined with the gradual performance improvements
Go has been making, make it fast enough to replace even some C and Fortran
codes.  So, let's go!

I'll update this page every now and then when I learn something new.

# Install

Most linux distributions package a version of go.
```bash
sudo install golang
```
In my case, Fedora Linux 35, that is ```go 1.16.15```, which could be a bit old.

## Using a specific Go version

Download a version at [the go website](https://go.dev), and extract it at a
handy location.  The default on my system is ```/usr/lib/golang```, but for my
installation I'm using ```$HOME/Code/go/goroot```.  This is the directory
containing the go compiler, toolchain, and supporting files.  Also create a
directory for installing downloaded or built packages; the default is
```$HOME/go```, but I prefer to keep my home directory clean and use
```$HOME/Code/go/gopath```.

```
$HOME
 └── Code
   └── go
     ├── goroot
     ├── go1.18.4.linux-amd64.tar.gz
     └── gopath
```

To start using the newly installed version, modify your environment (you should
probably add this to you .bashrc or something):
```bash
export GOROOT=$HOME/Code/go/goroot
export GOPATH=$HOME/Code/go/gopath

export PATH=$GOROOT/bin:$GOPATH/bin:$PATH
```

## Packages

Downloading and installing packages is done using the ```go``` command.  Install
dependencies to your current code (ie. module) using [go get](https://pkg.go.dev/cmd/go#hdr-Add_dependencies_to_current_module_and_install_them)
Install compiled packages using [go install](https://pkg.go.dev/cmd/go#hdr-Compile_and_install_packages_and_dependencies)

## Virtual environment

Go does not use virtual environments like python has; setting ```$GOROOT``` and
```$GOPATH```, and your shell's ```$PATH``` are all that is needed.

Projects are called ```modules```, and sort-of correspond to a repository. To
start a new project, create a new github repo.  For example, I've created a new
github repository called ```gostart```, located here
```https://github.com/jiskattema/gostart```.

Then check it out, and initialize a module:
```bash
mkdir gostart
cd gostart
go mod init github.com/jiskattema/gostart
```
Details are [here](https://go.dev/doc/tutorial/create-module), and some best
practices are described [here](https://stackoverflow.com/a/57314494/11210494).

Note that it is possible to rename a module by search-and-replacing the
```github.com/jiskattema/gostart``` string in all import statements and in the
```go.mod``` file.

# Write code

## Project layout

For really simple projects, a single ```main.go``` and ```go.mod``` file are
sufficient.  For a more extensive discussion see this
[community attempt at standarization](https://github.com/golang-standards/project-layout)

## Highlighting

I'm using vim's default Go syntax highlighting.

## Linting

Vim ALE supports several linters (check with ```:ALEInfo```), including
```gofmt```, ```goimports```, and ```golint```.  You can run any of those using
```:ALEFix <tool>```.

## Language server

Install with:
```bash
go install golang.org/x/tools/gopls@latest
```

## Logging and Debugging

A basic logging module is included in the [standard libraray](https://pkg.go.dev/log).

## Running

```bash
go run main.go
```

## Testing

Tests are in files called ```*_test.go```, and function to run should be called
```TestXxx```.

To run all tests run:
```bash
go test
```

For a step-by-step introduction, including test coverage, see [this blogpost](https://ieftimov.com/posts/testing-in-go-go-test/).

The ```testing``` package from the standard library can also do benchmarking and
fuzzing, [details are here](https://pkg.go.dev/testing#Examples).

## Packaging

```bash
go build main.go
```
builds the stand-alone binary executable.

# Interactive use

Go is not designed for interactive use.  Useability improvements in testing and
documentation should reduce the need for a REPL loop.  Compilation should be
fast enough not to be an issue.

# Recommended packages

