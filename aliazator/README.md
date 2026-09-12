## About

[Aliazator](https://github.com/javier-lopez/shundle-plugins/tree/master/aliazator) is a plugin for [Shundle](https://github.com/javier-lopez/shundle) which manages [aliases](http://en.wikipedia.org/wiki/Alias_%28command%29).

<p align="center">
<img src="http://javier.io/assets/img/aliazator.gif" alt="shundle"/>
</p>

## Quick start

1. Add [aliazator](https://github.com/javier-lopez/shundle-plugins/tree/master/aliazator) to your shundle configuration:

   ```sh
   Bundle='javier-lopez/shundle-plugins/aliazator'
   ```

2. Install it:

   ```
   $ shundle install
   ```

3. Reload your configuration

   ```
   $ . ~/.bashrc
   $ aliazator list
   ```

   Installation requires [Shundle](https://github.com/javier-lopez/shundle) and triggers [Git](http://git-scm.com/).

## Usage

[Aliazator](https://github.com/javier-lopez/shundle-plugins/tree/master/aliazator) provides and help to manage aliases. By default it try to load as few aliases as possible, however it provide hundred of aliases for dozens of commands. More aliases are welcome, fork and push back!

[Aliazator](https://github.com/javier-lopez/shundle-plugins/tree/master/aliazator) organices aliases per command, for instance git aliases are located at `aliases/extra/git.aliases` and can be enabled by running:

   ```
   $ aliazator enable git
   ```

For unloading the same git set, run:

   ```
   $ aliazator disable git
   ```

At every momment, aliazator can list which alias sets are enable:

   ```
   $ aliazator list
     meta
       none
      +minimal
       installed
       all

     options
      +custom
      +general
      +linux-gnu
       ...
   ```

[Aliazator](https://github.com/javier-lopez/shundle-plugins/tree/master/aliazator) support meta-sets (sets who contain other sets), by default it enable the `minimal` meta-set, which enable the `custom` (softlink to $HOME/.aliases), `general` and `linux-gnu` sets. To list which aliases are defined at each set use the `list` subcommand, e.g. for listing aliases defined in the `general` set:

   ```
   $ aliazator list general
   ```

To modify which aliases are loaded by default define `ALIAZATOR_PLUGINS` in your shell configuration file (~/.bashrc for bash, .zshrc for zsh and so on):

   ```sh
   ALIAZATOR_PLUGINS="minimal"
   ```

`ALIAZATOR_PLUGINS` recognize the following options:

- none
 - no alias is loaded
- minimal (default)
 - loads custom,general,platform-specific (linux-gnu on linux, osx on mac os)
- installed 
 - loads aliases for installed applications, for instance if git is available, git aliases will be loaded
- all
 - loads all aliases, even aliases for applications which may be not installed
- custom
 - let you define which specific aliases to load, e.g. custom:minimal,git,vim (will load the minimal meta-set plus git & vim aliases)

### Aliases never hide commands

An alias named like an existing command is only created when it decorates that
same command, e.g. `alias ls='ls --color=auto'` or `alias sudo='sudo '`. An
alias that would run something else under a command's name is skipped: with
`dd` installed, `alias dd='dot diff'` is not created, and neither is
`alias gs='git status'` when Ghostscript provides `gs`.

The check runs on the machine that loads the aliases, so a set can load fully
on one system and partially on another. Skipped names are listed in
`ALIAZATOR_SKIPPED`:

   ```
   $ echo "${ALIAZATOR_SKIPPED}"
   install,gs,ussh,vi,size,
   ```

If an earlier set had already defined a skipped name, that earlier definition
is kept.

To let an alias hide a command on purpose, list its name in `ALIAZATOR_SHADOW`:

   ```sh
   ALIAZATOR_SHADOW="size install gs"
   ```

An alias only exists in the interactive shell, so scripts and `make` keep
running the real command.

### Which aliases are used

`aliazator stats` counts aliases in the shell history (`ETERNALIZE_PATH` when
eternalize is loaded, `HISTFILE` otherwise): every command position counts,
including the word after `sudo`. Without arguments it prints used/defined per
set (`+` marks the loaded ones); with a set, every alias in it, most used
first:

   ```
   $ aliazator stats
   $ aliazator stats git
   ```

### Which aliases are missing

`aliazator suggest [n]` is the reverse of `stats`: it reads the same history and
lists the command shapes you repeat that no alias covers, most repeated first.
It groups by the first two words, so `git push origin a` and `git push origin b`
count as one habit, and it proposes a name from their initials, growing it by
one letter while the name is taken by an alias, a command or a function in this
shell. A shape needs 3 uses and 10 characters to show up; the word after `sudo`
counts as the command, so `sudo apt install` suggests an alias for
`apt install` (with `alias sudo='sudo '` loaded, `sudo <alias>` still expands).

It never writes: every line is ready to paste into the `custom` set
(`~/.aliases`).

   ```
   $ aliazator suggest
   history: /home/m/.eternalize-data
      206  alias br='bash scripts/run.sh'     #e.g. bash scripts/run.sh
       48  alias dsto='docker stop'           #e.g. docker stop
   ```

Command lookups ignore WSL's Windows directories (`/mnt/<drive>/...` in
`PATH`): a failed lookup costs ~40ms there against ~0.1ms in Linux
directories, and aliazator runs hundreds of them.

## Contributors

See [Aliazator contributors](https://github.com/javier-lopez/shundle-plugins/graphs/contributors)

*Thank you!*

## Inspiration and ideas from

* [bash-it](https://github.com/revans/bash-it)
* [alias.sh](http://alias.sh/)

## Also

* Aliazator was developed and tested with [Bash](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) 4.2 on Linux
* Aliazator will try to run in as many platforms & shells as possible
* Aliazator tries to be as [KISS](http://en.wikipedia.org/wiki/KISS_principle) as possible

## TODO:
[Aliazator](https://github.com/javier-lopez/shundle-plugins/tree/master/aliazator) is a work in progress, so any ideas and patches are appreciated.

* write documentation
* tests
* add colors
* add alias.sh support
* improve error handling
* make it rock!
