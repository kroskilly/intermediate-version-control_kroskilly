---
layout: page
title: Configuring Git
order: 4
session: 1
length: 10
toc: true
adapted: false
---

## Configuring Git

For this course we will go through the commands used in our tutorial, starting with the configuration commands, `git config`.

## Hello!

### Getting help in Git

We are going to be looking at some of the options when using git's subcommand `config`.
We can see the built-in help for this, or any git command, with the `-h` argument:

``` sh
git config -h
```

This should print the contents of the command's help to the terminal screen.
Other ways of seeing this information are `git config --help` (opens a browser on windows), `man git-config`, or through the online help pages through an internet search.

### Configuration file

When we first started with git (probably before this course) we had to add our name and e-mail.
This was to ensure that our details were applied to all of our commits.
But where was this information stored?

We can see all of the configuration options that git is aware of, and where they are stored, with

``` sh
git config --list --show-origin --show-scope
```

All of our global configuration (where the name and e-mail are stored) are saved in a `.gitconfig` file, typically found in your user home directory.
We can see the contents of this file from the terminal:

``` sh
cat ~/.gitconfig
```

If you want to bring your git configurations to a new system or make use of some else's, we can simply move this file.

While changes can be made to this file, we shall stick to using the command.

### Setting the Default Editor

There are times where git will open a text editor for us.
We can tell git what program to invoke in these situations.
For this course we will be using the terminal based editor nano.

To set the editor used by git to nano, we enter the `config` command

``` sh
git config --global core.editor nano
```

### Setting Aliases

Over the course of the tutorial we saw some long commands, and other commands repeated again and again.
One extremely helpful trick we can use, is to set aliases to speed us up for commands we use often.

The command I use most often is probably

``` sh
git status
```

This tells you what branch you're on, what staged or unstaged changes have been made to the code, and gives information on the relative status to any tracked branches on the remote.
Whilst it is already a short command, I type it enough that it's helpful to make it even shorter.

We can assign an *alias*, so typing `git st` is equivalent to typing `git status`.

``` sh
git config --global alias.st status
```

We can now use our new alias `st` with the exact same result as `status`

``` sh
git st
```

To set an alias with the arguments included, wrap the whole command in apostrophes:
for example, to make a new command that lists our global settings, we could type

``` sh
git config --global alias.list-config 'config --list --global'
```

If we use this new command we should now see the extra aliases in the output.

``` sh
$ git list-config
user.name=Jane Doe
user.email=j.doe1@exeter.ac.uk
alias.st=status
alias.list-config=config --list --global
# other options applied when you installed git
```

### Summary

We have used the `config` command to list and set settings, and specifically to add aliases to speed us up.
As you get more familiar with git, you will find commands that you use time and time again with the same arguments.
Be sure to set them as aliases.

We can even use aliases to run external scripts as if they were git commands.
To do this, precede the aliased command with `!`, for example

``` sh
git config --global alias.cat-config '!cat ~/.gitconfig'
```

### Exercise: Make an alias for log

Use `git config` to add an alias called `mylog` is equivalent to typing out

``` sh
git log --oneline --all --graph
```

Test it with

``` sh
git mylog
```

#### Solution

``` sh
git config --global alias.mylog 'log --oneline --all --graph'
```
