# Entrée

A way to version control and manage your [entr](http://entrproject.org/) watchers.

**Why?**

As soon as I reboot my machine, I have some watchers that I always start, this makes it more manageable
than having to retype the commands all of the time.

It also enables version controlling of more dotfiles because y'know, Linux.

## Installation

```
git clone https://github.com/joereynolds/entree
cd entree
./install.sh
```
This installs `entree` and the bash tab completion for `entree`.


## .entreerc

Your `.entreerc` is where you store all your watches, it's in a similar format to an ini file and is located in your home directory (`~/.entreerc`). Here's an example:

```
# Located in ~/.entreerc

[run-build]
find . -not -path "./node_modules/*" | entr npm run build

[detect-dead-css]
ls ~/programs/mort/test/fixtures/*.css | entr mort -vf /_
```

### Syntax

Syntax for the `~/.entreerc` is very simple. just add the name of your watcher and on the line beneath, the command for entr to run.

Anything else is considered a comment so feel free to heavily annotate your `~/.entreerc`.


### Commands 

With the above `~/.entreerc` in mind, here are the commands available to run:

(entree supports tab completion, use it.)

**Edit**

Opens up your `~/.entreerc` in your `$EDITOR` or vim if you don't have one.

**List**

Lists all watchers in your `~/.entreerc`

```
$ entree list
run-build
detect-dead-css
```

**Show**

Shows the watcher and what it does

```
$ entree show detect-dead-css
[detect-dead-css]
ls ~/programs/mort/test/fixtures/*.css | entr mort -vf /_
```

**Watch**

Starts a watcher by the given name

```
$ entree watch run-build
Executing ls ~/programs/mort/test/fixtures/*.css | entr npm run build
```

**Help**

Shows help  

```
$ entree help
usage: entree [subcommand]
SUBCOMMANDS:
  list    Show all watchers
  show    Show what a specific watcher does
  watch   Begin the command for that watcher
```
