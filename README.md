# Shell Shenanigans
This repository holds a slowly growing list of commands, some of the results of
me playing around with Posix shell and/or Bash. Some are actually useful (and I
do actually use them), others less so. Some are Debian-specific. Some of them
are based on my posts in the German [debianforum.de](https://debianforum.de/).

## Usage Reminder (to self)
Use [`stow`](https://www.gnu.org/software/stow/) to link the commands into `~/bin`:
```sh
shell-shenanigans$ stow -t ~ stow
```
There is a `.stowrc` with helpful options.
