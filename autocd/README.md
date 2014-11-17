## About

[Autocd](https://github.com/chilicuil/shundle-plugins/tree/master/autocd) is a plugin for [Shundle](https://github.com/chilicuil/shundle) who helps to launch terminal sessions "from here"

<p align="center">
<img src="http://javier.io/assets/img/autocd-1.gif" alt="autocd"/>
</p>

## Quick start

1. Add [autocd](https://github.com/chilicuil/shundle-plugins/tree/master/autocd) to your shundle configuration:

   ```sh
   Bundle='chilicuil/shundle-plugins/autocd'
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

[Autocd](https://github.com/chilicuil/shundle-plugins/tree/master/autocd) stores the current working directory on every enter (just as history does anyway) and uses the result to jump to it when a new bash session is open.

After completing the installation, no action is required, it will start logging every single change in the working directory, including those who are executed from different sessions.

**AUTOCD_FILE**

By default autocd uses /tmp to store data, this allows to start fresh after every reboot, if you prefer to make the behavior permanent (even after reboots) change it to a non volatile path

    AUTOCD_FILE="/tmp/autocd.59YlpZ50"

## Contributors

See [autocd contributors](https://github.com/chilicuil/shundle-plugins/graphs/contributors)

*Thank you!*

## Also

* autocd was developed and tested with [Bash](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) 4.2 and [tabbedex](https://github.com/minos-org/minos-tools/blob/master/urxvt/tabbedex) on Linux
* autocd will try to run in as many platforms & shells as possible
* autocd tries to be as [KISS](http://en.wikipedia.org/wiki/KISS_principle) as possible

## TODO:

[autocd](https://github.com/chilicuil/shundle-plugins/tree/master/autocd) is a work in progress, so any ideas and patches are appreciated.

* write documentation
* tests
* make it rock!
