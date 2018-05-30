# Entree

A wrapper for `entr`, the file watcher.

## .entreerc

This is where you store your watchers, it's in the format of an ini file, here's an example:


```
# Located in ~/.entreerc

[run-build]
ls ~/programs/mort/test/fixtures/*.css | entr npm run build

[detect-dead-css]
ls ~/programs/mort/test/fixtures/*.css | entr mort -vf /_
```

With the above in mind, here are the commands available to run  


### Syntax

Syntax for the `~/.enteerc` is very simple. just add the name of your watcher and on the line beneath, the command for entr to run.

Anything else is considered a comment so feel free to heavily annotate your `~/.enteerc`.


### Commands 
**List**

Lists all watchers in your `~/.entreerc`

```
$ entree list
run-build
detect-dead-css
```

**Show**

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
