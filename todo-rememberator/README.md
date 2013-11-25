## About

[Todo-Rememberator](https://github.com/chilicuil/shundle-plugins/tree/master/todo-rememberator) is a plugin for [Shundle](https://github.com/chilicuil/shundle) who print todo items at the begining of a new terminal session at random intervals.

<p align="center">
<img src="http://javier.io/assets/img/todo-1.png" alt="todo"/>
</p>

## Quick start

1. Add [Todo-Rememberator](https://github.com/chilicuil/shundle-plugins/tree/master/todo-rememberator) to your shundle configuration:

   ```sh
   Bundle='chilicuil/shundle-plugins/todo-rememberator'
   ```

2. Install it:

   ```
   $ shundle install
   ```

3. Reload your configuration

   ```
   $ . ~/.bashrc
   ```

[Todo-Rememberator](https://github.com/chilicuil/shundle-plugins/tree/master/todo-rememberator) requires [todo](http://todotxt.com/)

## Usage

[Todo-Rememberator](https://github.com/chilicuil/shundle-plugins/tree/master/todo-rememberator) by default will print todo items at an average speed 1/5 (once for every 5 new cli sessions). If you prefer to modify how often it gets displayed you can set the `REMEMBERATOREVERY` variable

   ```sh
   REMEMBERATOREVERY=10
   ```

It will now get printed on an average 1/10.

## Contributors

See [Todo-Rememberator contributors](https://github.com/chilicuil/shundle-plugins/graphs/contributors)

*Thank you!*

## Also

* Todo-Rememberator was developed and tested with [Bash](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) 4.2 on Linux
* Todo-Rememberator will try to run in as many platforms & shells as possible
* Todo-Rememberator tries to be as [KISS](http://en.wikipedia.org/wiki/KISS_principle) as possible

## TODO:
[Todo-Rememberator](https://github.com/chilicuil/shundle-plugins/tree/master/todo-rememberator) is a work in progress, so any ideas and patches are appreciated.

* support more todo applications
* tests
* make it rock!
