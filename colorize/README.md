## About

[Colorize](https://github.com/chilicuil/shundle-plugins/tree/master/colorize) is a plugin for [Shundle](https://github.com/chilicuil/shundle) who manages ps and other color variables.

<p align="center">
<img src="http://javier.io/assets/img/colorize.gif" alt="colorize"/>
</p>

## Quick start

1. Add [colorize](https://github.com/chilicuil/shundle-plugins/tree/master/colorize) to your shundle configuration:

   ```sh
   Bundle='chilicuil/shundle-plugins/colorize'
   ```

   And optionally to **~/.Xresources** or **~/.Xdefaults** to syncronize other X11 cli applications

   ```
   #include ".Xdefaults-theme-colorize"
   ```

2. Install it:

   ```
   $ shundle install
   ```

3. Reload your configuration

   ```
   $ . ~/.bashrc
   ```

## Usage

[Colorize](https://github.com/chilicuil/shundle-plugins/tree/master/colorize) provides color themes for your cli needs. More themes are welcome, fork and push back!

By default it will enable the `yujie`(ps), `default-dark`(theme) and `sky`(utils) items, but you set|define your favorites:

Use the `colorize` command to list, preview and study the color themes:

   ```
   $ colorize list #shortcut: colorize l
   $ colorize enable italian #shorcut: colorize e italian
   $ colorize enable theme brewer-dark #shortcut: colorize e t brewer-dark
   $ colorize show utils sky #shortcut: colorize s u sky
   ```

Colorthemes are separated by category:

 1. **ps**: control the ps variables (make your prompt awesome ;)
 2. **theme**: define the general colors for your terminal
 3. **utils**: set a theme for special utilities such as `ls`, `less`, `grep`, etc

Once you decide which theme to use, define `COLORIZE_PS`, `COLORIZE_THEME` and `COLORIZE_UTILS` in your shell configuration file (~/.bashrc for bash, .zshrc for zsh and so on):

   ```sh
   Bundle="github:chilicuil/shundle-plugins/colorize"
       COLORIZE_PS="yujie"
       #COLORIZE_PS="$HOME/you-can-also-set-custom-file"
       COLORIZE_THEME="default-black"
       #COLORIZE_THEME="$HOME/you-can-also-set-custom-file"
       COLORIZE_UTILS="sky"
       #COLORIZE_UTILS="$HOME/you-can-also-set-custom-file"
   ```

## Contributors

See [Colorize contributors](https://github.com/chilicuil/shundle-plugins/graphs/contributors)

*Thank you!*

## Also

* Colorize was developed and tested with [Bash](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) 4.2 on Linux
* Colorize will try to run in as many platforms & shells as possible
* Colorize tries to be as [KISS](http://en.wikipedia.org/wiki/KISS_principle) as possible

## TODO:
[Colorize](https://github.com/chilicuil/shundle-plugins/tree/master/colorize) is a work in progress, so any ideas and patches are appreciated.

* write documentation
* tests
* add more themes
* make it rock!
