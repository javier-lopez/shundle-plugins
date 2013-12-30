## About

[Colorize](https://github.com/chilicuil/shundle-plugins/tree/master/colorize) is a plugin for [Shundle](https://github.com/chilicuil/shundle) who manages ps and other color variables.

## Quick start

1. Add [colorize](https://github.com/chilicuil/shundle-plugins/tree/master/colorize) to your shundle configuration:

   ```sh
   Bundle='chilicuil/shundle-plugins/colorize'
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

[Colorize](https://github.com/chilicuil/shundle-plugins/tree/master/colorize) provides ps themes for your cli needs. More themes are welcome, fork and push back!

By default it will enable the `yujie` ps sheme, you can however choose from a bunch of themes.

Use the `colorize` command to list and preview colorthemes:

   ```
   $ colorize list
   $ colorize enable italian
   ```

Once you decide which theme to use, define `COLORIZE_THEME` and `COLORIZE_PS` in your shell configuration file (~/.bashrc for bash, .zshrc for zsh and so on):

   ```sh
   COLORIZE_THEME="blacky"
   COLORIZE_PS="yujie"
   ```

`COLORIZE_THEME` recognize the following options:

- none
 - no colorshme loaded
- blacky (default)
 - define ls,man,less output

`COLORIZE_PS` recognize the following options:

- approval
<p align="center">
<img src="http://javier.io/assets/img/colorize-approval.png" alt="approval"/>
</p>
- arch
<p align="center">
<img src="http://javier.io/assets/img/colorize-arch.png" alt="arch"/>
</p>
- bretterpstra
<p align="center">
<img src="http://javier.io/assets/img/colorize-bretterpstra.png" alt="bretterpstra"/>
</p>
- delicious
<p align="center">
<img src="http://javier.io/assets/img/colorize-delicious.png" alt="delicious"/>
</p>
- dhampir
<p align="center">
<img src="http://javier.io/assets/img/colorize-dhampir.png" alt="dhampir"/>
</p>
- flex
<p align="center">
<img src="http://javier.io/assets/img/colorize-flex.png.png" alt="flex"/>
</p>
- italian
<p align="center">
<img src="http://javier.io/assets/img/colorize-italian.png" alt="italian"/>
</p>
- load
<p align="center">
<img src="http://javier.io/assets/img/colorize-load.png" alt="load"/>
</p>
- minimal
<p align="center">
<img src="http://javier.io/assets/img/colorize-minimal.png" alt="minimal"/>
</p>
- msdos
<p align="center">
<img src="http://javier.io/assets/img/colorize-msdos.png" alt="msdos"/>
</p>
- prome7hius
<p align="center">
<img src="http://javier.io/assets/img/colorize-prome7hius.png" alt="prome7hius"/>
</p>
- sergio
<p align="center">
<img src="http://javier.io/assets/img/colorize-sergio.png" alt="sergio"/>
</p>
- tonka
<p align="center">
<img src="http://javier.io/assets/img/colorize-tonka.png" alt="tonka"/>
</p>
- walk
<p align="center">
<img src="http://javier.io/assets/img/colorize-walk.png" alt="walk"/>
</p>
- yujie
<p align="center">
<img src="http://javier.io/assets/img/colorize-yujie.png" alt="yujie"/>
</p>
- zork
<p align="center">
<img src="http://javier.io/assets/img/colorize-zork.png" alt="zork"/>
</p>

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
