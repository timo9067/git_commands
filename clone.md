## The `git` **clone** command

### Description
---
Although humans can't quite clone yet, git sure can, and a great tool it is. Following are a few of its <u>capabilities</u>:

Git's **clone** command has *one* function at its core: clone a repository into a new directory. However, there are many flavors to this tool.

It can create remote-tracking branches for each branch in a cloned repository, and creates and checks out an inital branch that is forked from the cloned repository's currently active branch, given some configuration.

### Options
---
- `-l, --local`

When the repository to clone from is on a local machine, this flag bypasses the normal "Git aware" transport mechanism and clones the repository by making a copy of HEAD and everything under objects and  refs directories.

- `-s, --shared`  

When the repository to clone is on the local machine, instead of using hard links, automatically setup **.git/objects/info/alternates** to share the objects with the source repository. The resulting repository starts out without any object of its own.

- `-q, --quiet`

Operate quietly. Progress is not reported to the standard error stream.

- `-v, --verbose`

Run verbosely. Does not affect the reporting of progress status to the standard error stream.

- `--progress`

Progress status is reported on the standard error stream by default when it is attached to a terminal, unless --quiet is specified. This flag forces progress status even if the standard error stream is not directed to a terminal.


- `-n, --no-checkout`

No checkout of HEAD is performed after the clone is complete.

### Examples
---
```git
$ git clone https://github.com/

$ git clone -l -s . ../copy

$ git clone -q

$ git clone  -v
```