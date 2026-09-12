## About

[Eternalize](https://github.com/javier-lopez/shundle-plugins/tree/master/eternalize) is a plugin for [Shundle](https://github.com/javier-lopez/shundle) who records an infinite history of executed commands.

<p align="center">
<img src="http://javier.io/assets/img/eternalize-1.png" alt="eternalize"/>
</p>

## Quick start

1. Add [eternalize](https://github.com/javier-lopez/shundle-plugins/tree/master/eternalize) to your shundle configuration:

   ```sh
   Bundle='javier-lopez/shundle-plugins/eternalize'
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

[Eternalize](https://github.com/javier-lopez/shundle-plugins/tree/master/eternalize) store an eternal history file across sessions from commands executed.

After completing the installation, no action is required, it will start logging every single command you enter from terminal emulators, including those who are executed from different sessions.

For looking at the eternal historial the `eternalize` alias is provided, it will open the eternal history file in the configured $EDITOR.

**ETERNALIZE_BIND**

The readline key sequence that searches the eternal file, empty by default so
readline's own `Ctrl-R` keeps working until you say otherwise:

   ```sh
   ETERNALIZE_BIND='"\C-r"'     #or '"\C-x\C-r"' to keep both
   ```

`Ctrl-R` searches only the current shell's memory; this one searches every
command every session ever ran. The pick lands in the edit buffer, cursor at
the end, for you to edit or run — `bind -x` is what allows that, by letting the
function write `READLINE_LINE`. With [fzf](https://github.com/junegunn/fzf)
installed it is a fuzzy finder seeded with whatever you had typed; without it,
a numbered menu of the 15 most recent unique matches. Bash only.

**ETERNALIZE_FZF_JUMP**

Inside the finder, this key **puts a number on every line you can see** and the
next key takes that one:

   ```sh
   ETERNALIZE_FZF_JUMP="ctrl-s"     #s for show
   ```

The numbers are the positions of the list as it stands, so they keep pointing
at what you are looking at however much you have typed — which is why they are
not printed permanently: fzf can only stamp a line with its position in the
*input*, and that stops matching the screen at the first keystroke.

`Ctrl-S` is XON/XOFF in a terminal, but fzf reads in raw mode so it gets there.
A multiplexer that insists on flow control is the case for changing this.

**ETERNALIZE_FZF_OPTS**

How the finder looks. Unset — the default — it is built on first use out of
[colorize](https://github.com/javier-lopez/shundle-plugins/tree/master/colorize)'s
slot numbers, so the finder wears the prompt's colours without ever knowing
which prompt is active. Change your `ps` theme or your `.theme` and the finder
follows; without colorize it falls back to the ANSI defaults.

| in the finder | takes the slot of | which in `yujie` is |
|---------------|-------------------|---------------------|
| the `eternalize>` prompt | `_CZ_N_USER`, the one `\u` wears | blue |
| what your search matched | `_CZ_N_ACCENT` — the accent is what stands out, and that is what this is | yellow |
| the pointer, **and the numbers** | `_CZ_N_OK`, the go-ahead colour | green |
| the counter, the header, the border | `_CZ_N_DIM` | grey |

fzf has no colour of its own for the jump labels — it paints them with the
pointer's — so that one entry decides both.

Colours are slot numbers and never hex — `-1` is the terminal's own — so:

   ```sh
   ETERNALIZE_FZF_OPTS="--color=16,fg:-1,bg:-1,hl:2,prompt:4,pointer:3"
   ETERNALIZE_FZF_OPTS=""           #or hand it over to your FZF_DEFAULT_OPTS
   ```

eternalize installs nothing. fzf ships a static binary per platform, so if you
want the fuzzy finder, fetch it from your shundle configuration with a
`PostInstall` line of your own — pick the asset that matches your machine:

   ```sh
   Bundle='gh:javier-lopez/shundle-plugins/eternalize'
       ETERNALIZE_BIND='"\C-r"'
       PostInstall='wget -qO- https://github.com/junegunn/fzf/releases/download/v0.74.4/fzf-0.74.4-linux_amd64.tar.gz | tar xz -C ~/.local/bin fzf && chmod +x ~/.local/bin/fzf'
   ```

**ETERNALIZE_IGNORE**

Commands not worth an eternal line, as glob patterns separated by commas:

   ```sh
   Bundle='javier-lopez/shundle-plugins/eternalize'
       ETERNALIZE_PATH="${HOME}/.eternalize-data"
       ETERNALIZE_IGNORE="cd,cd *,ls,ls *,pwd,exit,clear,history,history *"
   ```

Set it to the empty string to record everything. The default deliberately holds
no alias of any other plugin: excluding an alias here is what makes
[aliazator](https://github.com/javier-lopez/shundle-plugins/tree/master/aliazator)'s
`stats` and `suggest` blind to the commands you run most, since they read this
file.

The command is taken from `history 1` by stripping its number with parameter
expansion, not by cutting a fixed field: `history` right-aligns that number in
five columns, so a field cut only works while it has three digits. With two it
returned the command with a blank in front, which no ignore pattern matched,
and past 999 it dropped the command's first word — `echo hola` was recorded as
`hola` — or the whole line.

<p align="center">
<img src="http://javier.io/assets/img/eternalize-2.png" alt="eternalize"/>
</p>

## Contributors

See [Eternalize contributors](https://github.com/javier-lopez/shundle-plugins/graphs/contributors)

*Thank you!*

## Also

* Eternalize was developed and tested with [Bash](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) 4.2 on Linux
* Eternalize will try to run in as many platforms & shells as possible
* Eternalize tries to be as [KISS](http://en.wikipedia.org/wiki/KISS_principle) as possible

## TODO:
[Eternalize](https://github.com/javier-lopez/shundle-plugins/tree/master/eternalize) is a work in progress, so any ideas and patches are appreciated.

* write documentation
* tests
* maybe an aux should be written to fetch faster previous commands or to integrate them to Ctrl-r
* make it rock!
