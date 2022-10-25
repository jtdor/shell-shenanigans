# Shell Shenanigans
This repository holds a slowly growing list of commands, some of the results of
me playing around with Posix shell and/or Bash. Some are actually useful (and I
do actually use them), others less so. Some are Debian-specific. Some of them
are based on my posts in the German [debianforum.de](https://debianforum.de/).

## Commands

## [`clean-channels-conf`](/clean-channels-conf)
Clean SD channels for which an HD channel of same name exists, and optionally
unwanted channels from a channels.conf. The cleaned channels.conf is printed to
standard out.

Prints a short help when called without arguments.

Example:
```console
user@host:~$ clean-channels-conf channels.conf unwanted_channels.list
Das Erste HD;ARD:330000:C0M256:C:6900:5101=27:0;5102=deu@106,5103=mis@106,5107=qks@106:5104:0:10301:1:1051:0
ZDF HD;ZDFvision:450000:C0M256:C:6900:6110=27:0;6120=deu@106,6121=mis@106,6123=mul@106:6130:0:11110:1:1079:0
…
```

## [`crawl`](/crawl)
Executes a command on multiple hosts via SSH. Has a short built-in help.

Example:
```console
user@host:~$ crawl -Pt localhost remotehost -- uptime
# localhost:
 15:44:20 up 6 days,  3:48,  1 user,  load average: 0,25, 0,88, 1,30

# remotehost:
 14:44:21 up 14 days,  3:47,  0 users,  load average: 0.29, 0.14, 0.14
```

## [`deb-peak-copyright`](/deb-peak-copyright)
Displays the copyright file (or any file, really) of Debian packages. Uses the
local file, if the package is installed, or downloads and extracts it first.

Example:
```console
user@host:~$ deb-peak-copyright dash libc6
[…]
```
The environment variable `copyright_path` can be set to the path of a different
file. The path can contain a `*` as a wildcard, e.g. as a placeholder for the
package name.


## [`showmd`](/showmd)
Quickly display a Markdown file (converted to HTML) in a browser. Watches the
Markdown file, updating the HTML file on changes.

Example:
```console
user@host:~$ showmd README.md
```

It might be overkill to use Python’s http.server in here. Just `open`ing the
HTML file would have done it.

## [`tempat`](/tempat)
Wrapper around `at` to make a job non-persistent, meaning it does not execute
after a reboot. Supports commands passed on standard input (same as `at` does),
but not with `-f`.

Requires `/run` to be mounted as a tmpfs (it generally is).

Example:
```console
root@host:~# tempat now + 1min
tempat> # Input command here
root@host:~# echo "touch /run/AT_WAS_HERE" | tempat now + 1min
```

## [`treeprint`](/treeprint)
Displays given words in a tree-like structure, using `tree`.

Example:
```console
user@host:~$ treeprint root node-a node-b node-b/node-c
root
├── node-a
└── node-b
    └── node-c
```

## Usage Reminder (to self)
Use [`stow`](https://www.gnu.org/software/stow/) to link the commands into `~/bin`:
```console
user@host:shell-shenanigans$ stow -t ~ stow
```
There is a `.stowrc` with helpful options.
