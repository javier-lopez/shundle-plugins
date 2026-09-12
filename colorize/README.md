## About

[Colorize](https://github.com/javier-lopez/shundle-plugins/tree/master/colorize) is a plugin for [Shundle](https://github.com/javier-lopez/shundle) who manages ps and other color variables.

<p align="center">
<img src="http://javier.io/assets/img/colorize.gif" alt="colorize"/>
</p>

## Quick start

1. Add [colorize](https://github.com/javier-lopez/shundle-plugins/tree/master/colorize) to your shundle configuration:

   ```sh
   Bundle='javier-lopez/shundle-plugins/colorize'
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

[Colorize](https://github.com/javier-lopez/shundle-plugins/tree/master/colorize) provides color themes for your cli needs. More themes are welcome, fork and push back!

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
   Bundle="github:javier-lopez/shundle-plugins/colorize"
       COLORIZE_PS="yujie"
       #COLORIZE_PS="$HOME/you-can-also-set-custom-file"
       COLORIZE_THEME="default-black"
       #COLORIZE_THEME="$HOME/you-can-also-set-custom-file"
       COLORIZE_UTILS="sky"
       #COLORIZE_UTILS="$HOME/you-can-also-set-custom-file"
   ```

## Writing a ps theme

Every theme is sourced after `core`, which leaves a palette and a set of
segments ready. `core` is a floor, not a ceiling: it saves you from writing
again what every prompt needs, and a theme is free to compute whatever else it
wants. If a theme becomes popular, whatever was reusable in it moves down here
— that is how `files` and `load` got in.

   ```sh
   _cz_use status pwd git
   PS1="${_CZ_USER}\u${_CZ_RESET} [\${_CZ_STATUS}${_CZ_RESET}:\${_CZ_PWD}\${_CZ_GIT}] \$ "
   ```

Colours go straight into `PS1` and expand once, when the theme builds it, so
they are written `${_CZ_USER}`. Segments are recomputed on every prompt, so
`PS1` has to keep them unexpanded: `\${_CZ_PWD}`.

**Palette** — the eight colours a terminal lets its theme redefine, plus the
three attributes. `_CZ_GREEN` is not a green: it is whatever green your
`.theme` decided on, so a prompt written with these follows the colour theme
instead of fighting it.

| variable | |
|----------|-|
| `_CZ_BLACK` `_CZ_RED` `_CZ_GREEN` `_CZ_YELLOW` | the eight colours |
| `_CZ_BLUE` `_CZ_MAGENTA` `_CZ_CYAN` `_CZ_WHITE` | |
| `_CZ_RESET` `_CZ_BOLD` `_CZ_DIM` | the attributes |

Say what a colour is *for* and not which one it is, so one line in a `.theme`
can move it:

| variable | paints | default |
|----------|--------|---------|
| `_CZ_OK` / `_CZ_ERR` | a command that worked / failed | green / red |
| `_CZ_USER` / `_CZ_HOST` | `\u` / `\h` | blue / green |
| `_CZ_PATH` / `_CZ_HOME` / `_CZ_SEP` | a path, its `~`, the `/` between | green / magenta / red |
| `_CZ_ABBR` | a path component that had to be cut | white |
| `_CZ_ACCENT` | whatever the theme wants to stand out | yellow |
| `_CZ_WHOAMI` | `\u`, but red when that user is root | `_CZ_USER` |
| `_CZ_ROOT` | not a colour: set when you are root | empty |

Anything the palette does not name: `$(_cz_color '38;5;208')`.

Each of those has a `_CZ_N_` twin holding the **slot number** — `_CZ_N_ACCENT`,
`_CZ_N_USER`, `_CZ_N_PATH`, … plus `_CZ_N_DIM` — and the escape above is built
from it. Move the number and the prompt moves:

   ```sh
   _CZ_N_ACCENT=5     #this theme's accent is magenta
   ```

The number is also the only form another program can use. A finder, a pager,
`ls`: they take slot numbers, a `.theme` repaints slots, so anything that asks
colorize *which slot is the accent* ends up wearing the same colours as the
prompt without ever knowing which prompt is active —
[eternalize](https://github.com/javier-lopez/shundle-plugins/tree/master/eternalize)'s
`Ctrl-R` finder does exactly that.

**Segments** — `_cz_use <module>...`:

| module   | leaves                                                    | costs         |
|----------|-----------------------------------------------------------|---------------|
| `status` | `_CZ_STATUS` (the exit code), `_CZ_MARK` (a ✓/✗ glyph)     | nothing       |
| `pwd`    | `_CZ_PWD`, `$HOME` as `~` and middle components abbreviated | nothing      |
| `git`    | `_CZ_GIT`, plus `_CZ_GIT_NAME`/`_CZ_GIT_DIRTY`/`_CZ_GIT_AHEAD`/`_CZ_GIT_BEHIND` | one `.git/HEAD` read, and a `git status` only under `COLORIZE_GITPROMPT=dirty` |
| `files`  | `_CZ_FILES`, `"24 files, 228Kb"`                           | one `ls`      |
| `chroot` | `_CZ_CHROOT`, computed once                                | nothing       |
| `load`   | `_CZ_LOAD`, the 1-minute load already coloured by severity  | nothing       |

Ask for everything the theme can draw. **The user decides which modules load**,
with `COLORIZE_MODULES`; a module that is off, or whose commands are missing,
leaves its variable empty and the prompt degrades instead of breaking.

   ```sh
   COLORIZE_MODULES="status pwd"   #unset means all of them
   ```

Customising what a segment looks like:

   ```sh
   _CZ_MARK_OK=":)" _CZ_MARK_ERR=":("       #or "" to show nothing on success
   _CZ_GIT_PRE=" on " _CZ_GIT_POST=""       #instead of " (branch)"
   COLORIZE_PWD_MAX=3                       #characters kept per middle component
   ```

A theme with a segment of its own writes it and registers it with
`_cz_hook <function>`, rather than touching `PROMPT_COMMAND`: the core's entry
has to stay first, because only the first entry still sees the exit status of
what you ran. `msdos.ps` is the whole of it — it wanted `C:\home\m` and nobody
else did:

   ```sh
   _msdos_pwd() { ... ; _MSDOS_PWD="..."; }
   _cz_hook _msdos_pwd
   PS1="C:\${_MSDOS_PWD}\\> "
   ```

## Contributors

See [Colorize contributors](https://github.com/javier-lopez/shundle-plugins/graphs/contributors)

*Thank you!*

## Also

* Colorize was developed and tested with [Bash](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) 4.2 on Linux
* Colorize will try to run in as many platforms & shells as possible
* Colorize tries to be as [KISS](http://en.wikipedia.org/wiki/KISS_principle) as possible

## TODO:
[Colorize](https://github.com/javier-lopez/shundle-plugins/tree/master/colorize) is a work in progress, so any ideas and patches are appreciated.

* write documentation
* tests
* add more themes
* make it rock!
