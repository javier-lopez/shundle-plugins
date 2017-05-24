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
