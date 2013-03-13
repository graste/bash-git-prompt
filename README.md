# Informative git prompt for bash

This prompt is a port of the "Informative git prompt for zsh" which you can find [here](https://github.com/olivierverdier/zsh-git-prompt)

A ``bash`` prompt that displays information about the current git repository.
In particular the branch name, difference with remote branch, number of files staged, changed, etc.

(an original idea from this [blog post][]).

The prompt in this repository looks like this atm:
``# 10:19:42 1045 0 (master ↑·2|● 3✚ 1…1) ~/projects/puppets $ ``

Means:
- ``#`` to prevent accidental execution of copy-pasted prompts
- current time including seconds to see execution time of commands
- history entry id for laster reference/reuse
- last command shell exit code
- awesome git status information
- current path

## Install

1. Download the ``~/.bash/`` files.
1. Source the file ``gitprompt.sh`` from your ``~/.bashrc`` config file (via `` . /path/to/gitprompt.sh`` or ``source /path/to/gitprompt.sh``)
1. Optionally configure your prompt in ``~/.bash/gitprompt.sh``. Easiest way is to set the variables PROMPT\_START and PROMPT\_END.
1. You may also redefine the function ``setGitPrompt`` to adapt it to your needs (to change the order in which the information is displayed).
1. Go in a git repository and test it!

**Enjoy!**

##  Prompt Structure

By default, the general appearance of the prompt is::

    (<branch> <branch tracking>|<local status>)

The symbols are as follows:

- Local Status Symbols
  - ``✔``: repository clean
  - ``●n``: there are ``n`` staged files
  - ``✖n``: there are ``n`` unmerged files
  - ``✚n``: there are ``n`` changed but *unstaged* files
  - ``…n``: there are ``n`` untracked files
- Branch Tracking Symbols
  - ``↑n``: ahead of remote by ``n`` commits
  - ``↓n``: behind remote by ``n`` commits
  - ``↓m↑n``: branches diverged, other by ``m`` commits, yours by ``n`` commits
- Branch Symbol:<br />
  	When the branch name starts with a colon ``:``, it means it's actually a hash, not a branch (although it should be pretty clear, unless you name your branches like hashes :-)

## Examples

The prompt may look like the following: 

* ``(master↑3|✚1)``: on branch ``master``, ahead of remote by 3 commits, 1 file changed but not staged
* ``(status|●2)``: on branch ``status``, 2 files staged
* ``(master|✚7…)``: on branch ``master``, 7 files changed, some files untracked
* ``(master|✖2✚3)``: on branch ``master``, 2 conflicts, 3 files changed
* ``(experimental↓2↑3|✔)``: on branch ``experimental``; your branch has diverged by 3 commits, remote by 2 commits; the repository is otherwise clean
* ``(:70c2952|✔)``: not on any branch; parent commit has hash ``70c2952``; the repository is otherwise clean

[blog post]: http://sebastiancelis.com/2009/nov/16/zsh-prompt-git-users/
