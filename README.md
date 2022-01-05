# Shell Shenanigans
This repository holds a slowly growing list of commands, some of the results of
me playing around with Posix shell and/or Bash. Some are actually useful (and I
do actually use them), others less so. Some are Debian-specific. Some of them
are based on my posts in the German [debianforum.de](https://debianforum.de/).

## Commands

## [`crawl`](/crawl)
Executes a command on multiple hosts via SSH. Has a short built-in help.

Example:
```sh
~$ crawl -Pt localhost remotehost -- uptime
# localhost:
 15:44:20 up 6 days,  3:48,  1 user,  load average: 0,25, 0,88, 1,30

# remotehost:
 14:44:21 up 14 days,  3:47,  0 users,  load average: 0.29, 0.14, 0.14
```

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


## [`showmd`](/showmd)
Quickly display a Markdown file (converted to HTML) in a browser. Watches the
Markdown file, updating the HTML file on changes.

Example:
```sh
~$ showmd README.md
```

It might be overkill to use Python’s http.server in here. Just `open`ing the
HTML file would have done it.

## [`treeprint`](/treeprint)
Displays given words in a tree-like structure, using `tree`.

Example:
```sh
$ treeprint root node-a node-b node-b/node-c
root
├── node-a
└── node-b
    └── node-c
```

## Usage Reminder (to self)
Use [`stow`](https://www.gnu.org/software/stow/) to link the commands into `~/bin`:
```sh
shell-shenanigans$ stow -t ~ stow
```
There is a `.stowrc` with helpful options.
