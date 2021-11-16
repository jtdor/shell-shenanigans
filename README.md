# Shell Shenanigans
This repository holds a slowly growing list of commands, some of the results of
me playing around with Posix shell and/or Bash. Some are actually useful (and I
do actually use them), others less so. Some are Debian-specific. Some of them
are based on my posts in the German [debianforum.de](https://debianforum.de/).

## Commands

## [`deb-peak-copyright`](/deb-peak-copyright)
Displays the copyright file (or any file, really) of Debian packages. Uses the
local file, if the package is installed, or downloads and extracts it first.

Example:
```sh
~$ deb-peak-copyright dash libc6
[…]
```
The environment variable `copyright_path` can be set to the path of a different
file. The path can contain a `*` as a wildcard, e.g. as a placeholder for the
package name.

## Usage Reminder (to self)
Use [`stow`](https://www.gnu.org/software/stow/) to link the commands into `~/bin`:
```sh
shell-shenanigans$ stow -t ~ stow
```
There is a `.stowrc` with helpful options.
