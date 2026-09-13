## About

[Runner](https://github.com/javier-lopez/shundle-plugins/tree/master/runner) is a plugin for [Shundle](https://github.com/javier-lopez/shundle) that gives every project the same short command, whatever it actually uses to run things.

## Quick start

1. Add [runner](https://github.com/javier-lopez/shundle-plugins/tree/master/runner) to your shundle configuration:

   ```sh
   Bundle='javier-lopez/shundle-plugins/runner'
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

   ```sh
   $ r dev up          #instead of: bash scripts/run.sh dev up
   $ r                 #which runner am I talking to?
   /home/m/gopana.app/scripts/run.sh
   ```

`r` walks up from wherever you stand until it finds something that runs
things, and then runs it **from the project root** — a compose file or a
Makefile names its paths relative to the project, not to the subdirectory you
happened to be in. Your own directory is left where it was.

The point is not the characters saved. It is that `r dev up` means the same
thing in every project you own, from any depth, so there is one thing to
remember instead of one per repository.

**RUNNER_FILES**

What counts as a runner, in order. The first one found wins, so a project's
own script comes before the generic build files:

   ```sh
   Bundle='javier-lopez/shundle-plugins/runner'
       RUNNER_FILES="scripts/run.sh run.sh justfile Justfile Makefile makefile Taskfile.yml package.json"
       RUNNER_NAME="r"     #the command's name, in case r is taken
   ```

A `.sh` runner is executed through its own shebang when it is executable, and
with `sh` when it is not: forcing `bash` on a script that asked for `sh` is how
a plugin breaks a project. The others go to `just`, `make`, `task` and
`npm run` respectively.

Called with no arguments it prints what it found and runs nothing. `make` with
no target builds, and deciding that you meant it is not this plugin's call.

## Contributors

See [Runner contributors](https://github.com/javier-lopez/shundle-plugins/graphs/contributors)

*Thank you!*

## Also

* Runner was developed and tested with [Bash](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) 5.2 on Linux
* Runner will try to run in as many platforms & shells as possible
* Runner tries to be as [KISS](http://en.wikipedia.org/wiki/KISS_principle) as possible

## TODO:
[Runner](https://github.com/javier-lopez/shundle-plugins/tree/master/runner) is a work in progress, so any ideas and patches are appreciated.

* completion for the subcommands each runner understands
* make it rock!
