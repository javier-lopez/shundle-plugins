## About

[Aliazator](https://github.com/chilicuil/shundle-plugins/tree/master/aliazator) is a plugin for [Shundle](https://github.com/chilicuil/shundle) which manages [aliases](http://en.wikipedia.org/wiki/Alias_%28command%29).

<p align="center">
<img src="http://javier.io/assets/img/aliazator.gif" alt="shundle"/>
</p>

## Quick start

1. Add [aliazator](https://github.com/chilicuil/shundle-plugins/tree/master/aliazator) to your shundle configuration:

   ```sh
   Bundle='chilicuil/shundle-plugins/aliazator'
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

   Installation requires [Shundle](https://github.com/chilicuil/shundle) and triggers [Git](http://git-scm.com/).

## Usage

[Aliazator](https://github.com/chilicuil/shundle-plugins/tree/master/aliazator) provides and help to manage aliases. By default it try to load as few aliases as possible, however it provide hundred of aliases for dozens of commands. More aliases are welcome, fork and push back!

[Aliazator](https://github.com/chilicuil/shundle-plugins/tree/master/aliazator) organices aliases per command, for instance git aliases are located at `aliases/extra/git.aliases` and can be enabled by running:

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

[Aliazator](https://github.com/chilicuil/shundle-plugins/tree/master/aliazator) support meta-sets (sets who contain other sets), by default it enable the `minimal` meta-set, which enable the `custom` (softlink to $HOME/.aliases), `general` and `linux-gnu` sets. To list which aliases are defined at each set use the `list` subcommand, e.g. for listing aliases defined in the `general` set:

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

## Contributors

See [Aliazator contributors](https://github.com/chilicuil/shundle-plugins/graphs/contributors)

*Thank you!*

## Inspiration and ideas from

* [bash-it](https://github.com/revans/bash-it)
* [alias.sh](http://alias.sh/)

## Also

* Aliazator was developed and tested with [Bash](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) 4.2 on Linux
* Aliazator will try to run in as many platforms & shells as possible
* Aliazator tries to be as [KISS](http://en.wikipedia.org/wiki/KISS_principle) as possible

## TODO:
[Aliazator](https://github.com/chilicuil/shundle-plugins/tree/master/aliazator) is a work in progress, so any ideas and patches are appreciated.

* write documentation
* tests
* add colors
* add alias.sh support
* improve error handling
* make it rock!
