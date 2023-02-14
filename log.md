## The `git` **log** command
*Examining logs, diﬀs and object information*

### Description
---
Shows the commit logs.

List commits that are reachable by following the parent links from the given commit(s), but exclude commits that are reachable from the one(s) given with a ^ in front of them. The output is given in reverse chronological order by default.

You can think of this as a set operation. Commits reachable from any of the commits given on the command line form a set, and then commits reachable from any of the ones given with ^ in front are subtracted from that set. The remaining commits are what comes out in the command’s output. Various other options and paths parameters can be used to further limit the result.

### Options
---

- `--follow`

>Continue listing the history of a file beyond renames (works only for a single file).

-   `branchB..branchA`

>show the commits on branchA that are not on branch>

-   `--follow [file]`

>show the commits that changed file, even across renames

- `--stat`

>Shows statistics about the log

### Examples
---
§ git log -a

§ git log --stat

### Usage
---
