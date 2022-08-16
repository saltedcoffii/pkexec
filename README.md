# pkexec

This software allows you to easily prefix your current or previous commands with `pkexec` (polkit exec) by double-tapping <kbd>esc</kbd>.

## What is `pkexec`?

`pkexec` allows the invoker to execute a command as another user using [polkit](https://www.freedesktop.org/wiki/Software/polkit/). It acts in a similar way to [sudo](https://sudo.ws/) and [doas](https://man.openbsd.org/doas).

Note that `pkexec` does not provide a command similar to `sudoedit` or `sudo -e` as far as I am aware.

## Installation

If you use [ohmyzsh](https://ohmyz.sh), simply add `pkexec` to the plugins array in your zshrc file, like so:

```zsh
plugins=(... pkexec)
```

## Usage

### Current typed commands

Say you have typed a long command and forgot to add `pkexec` in front:

```console
$ apt-get install build-essential
```

By pressing the <kbd>esc</kbd> key twice, you will have the same command with `pkexec` prefixed without typing:

```console
$ pkexec apt-get install build-essential
```

### Previous executed commands

Say you want to delete a system file and denied:

```console
$ rm some-system-file.txt
-su: some-system-file.txt: Permission denied
$
```

By pressing the <kbd>esc</kbd> key twice, you will have the same command with `pkexec` prefixed without typing:

```console
$ rm some-system-file.txt
-su: some-system-file.txt: Permission denied
$ pkexec rm some-system-file.txt
(password prompt will appear on screen)
$
```

The same happens for file editing, as told before.

## Key binding

By default, the `pkexec` plugin uses <kbd>esc</kbd><kbd>esc</kbd> as the trigger.
If you want to change it, you can use the `bindkey` command to bind it to a different key:

```sh
bindkey -M emacs '<seq>' sudo-command-line
bindkey -M vicmd '<seq>' sudo-command-line
bindkey -M viins '<seq>' sudo-command-line
```

where `<seq>` is the sequence you want to use. You can find the keyboard sequence
by running `cat` and pressing the keyboard combination you want to use.

## Contributing

First off, please star the project! It helps more people find it on GitHub.

If you have an issue with the software, please check to see if your issue has already been reported [here](https://github.com/saltedcoffii/pkexec/issues/). If not, feel free to open a new issue.

Do you have an idea to improve the software? [Pull requests](https://github.com/saltedcoffii/pkexec/pulls) are incredibly welcome and helpful. Not sure how to start a pull request? [This article](https://docs.github.com/en/pull-requests) in GitHub Docs can get you started.

## License and Legal
Thank you to the [ohmyzsh](https://ohmyz.sh/) project and its contributors for making the [sudo plugin](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/sudo) from which this plugin is forked.

I have retained the original plugin's MIT License. See [COPYING.md](https://github.com/saltedcoffii/pkexec/blob/master/COPYING.md) for details.

<a rel="license" href="https://mit-license.org/"><img alt="MIT License" style="border-width:0" src="https://upload.wikimedia.org/wikipedia/commons/0/0c/MIT_logo.svg" height="31" /></a>
