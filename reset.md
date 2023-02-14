## The `git -reset` command
Reset current HEAD to the specified state

``` 
git reset [-q] [<tree-ish>] [--] <pathspec>…​
git reset [-q] [--pathspec-from-file=<file> [--pathspec-file-nul]] [<tree-ish>]
git reset (--patch | -p) [<tree-ish>] [--] [<pathspec>…​]
git reset [--soft | --mixed [-N] | --hard | --merge | --keep] [-q] [<commit>]
```

### Descripton
____
In the first three forms, copy entries from `<tree-ish>` to the index. In the last form, set the current branch head (`HEAD`) to `<commit>` , optionally modifying index and working tree to match. The `<tree-ish>/<commit>` defaults to `HEAD` in all forms.

```bash 
git reset [-q] [<tree-ish>] [--] <pathspec>…​
git reset [-q] [--pathspec-from-file=<file> [--pathspec-file-nul]] [<tree-ish>]
```

These forms reset the index entries for all paths that match the `<pathspec>` to their state at `<tree-ish>`. (It does not affect the working tree or the current branch.)

This means that `git reset <pathspec>` is the opposite of `git add <pathspec>`. This command is equivalent to `git restore [--source=<tree-ish>] --staged <pathspec>....`

After running `git reset <pathspec>` to update the index entry, you can use git-restore to check the contents out of the index to the working tree. Alternatively, using git-restore and specifying a commit with `--source`, you can copy the contents of a path out of a commit to the index and to the working tree in one go.

- `git reset (--patch | -p) [<tree-ish>] [--] [<pathspec>…​]`

Interactively select hunks in the difference between the index and `<tree-ish>` (defaults to `HEAD`). The chosen hunks are applied in reverse to the index.

This means that `git reset -p` is the opposite of `git add -p`, i.e. you can use it to selectively reset hunks. See the “Interactive Mode” section of git-add to learn how to operate the `--patch` mode.

- `git reset [<mode>] [<commit>]`

This form resets the current branch head to `<commit>` and possibly updates the index (resetting it to the tree of `<commit>`) and the working tree depending on `<mode>`. If `<mode>` is omitted, defaults to `--mixed`. The `<mode>` must be one of the following:

- `--soft`

Does not touch the index file or the working tree at all (but resets the head to `<commit>`, just like all modes do). This leaves all your changed files "Changes to be committed", as git status would put it.

- `--mixed`

Resets the index but not the working tree (i.e., the changed files are preserved but not marked for commit) and reports what has not been updated. This is the default action.

If `-N` is specified, removed paths are marked as intent-to-add.

- `--hard`

Resets the index and working tree. Any changes to tracked files in the working tree since `<commit>` are discarded. Any untracked files or directories in the way of writing any tracked files are simply deleted.

- `--merge`

Resets the index and updates the files in the working tree that are different between `<commit>` and `HEAD`, but keeps those which are different between the index and working tree (i.e. which have changes which have not been added). If a file that is different between `<commit>` and the index has unstaged changes, reset is aborted.

In other words, `--merge` does something like a git `read-tree -u -m <commit>`, but carries forward unmerged index entries.

- `--keep`

Resets index entries and updates files in the working tree that are different between `<commit>` and `HEAD`. If a file that is different between `<commit>` and `HEAD` has local changes, reset is aborted.

- `--[no-]recurse-submodules`

When the working tree is updated, using `--recurse-submodules` will also recursively reset the working tree of all active submodules according to the commit recorded in the superproject, also setting the submodules' HEAD to be detached at that commit.


### Options
___
- `-q`, `--quiet`

Be quiet, only report errors.

- `--refresh`, `--no-refresh`

Refresh the index after a mixed reset. Enabled by default.

- `--pathspec-from-file=<file>`

Pathspec is passed in `<file>` instead of commandline args. If `<file>` is exactly - then standard input is used. Pathspec elements are separated by LF or CR/LF. Pathspec elements can be quoted as explained for the configuration variable `core.quotePath`. See also `--pathspec-file-nul` and global `--literal-pathspecs`.

- `--pathspec-file-nul`

Only meaningful with --pathspec-from-file. Pathspec elements are separated with NUL character and all other characters are taken literally (including newlines and quotes).

- `--`

Do not interpret any more arguments as options.

`<pathspec>…​`
Limits the paths affected by the operation.


### Examples
___

#### Undo add
```sh
$ edit                                     (1)
$ git add frotz.c filfre.c
$ mailx                                    (2)
$ git reset                                (3)
$ git pull git://info.example.com/ nitfol  (4)
```

1. You are happily working on something, and find the changes in these files are in good order. You do not want to see them when you run `git diff`, because you plan to work on other files and changes with these files are distracting.

2. Somebody asks you to pull, and the changes sound worthy of merging.

3. However, you already dirtied the index (i.e. your index does not match the `HEAD` commit). But you know the pull you are going to make does not affect `frotz.c` or `filfre.c`, so you revert the index changes for these two files. Your changes in working tree remain there.

4. Then you can pull and merge, leaving frotz.c and filfre.c changes still in the working tree.

#### Undo a commit and redo

```sh
$ git commit ...
$ git reset --soft HEAD^      (1)
$ edit                        (2)
$ git commit -a -c ORIG_HEAD  (3)
```
1. This is most often done when you remembered what you just committed is incomplete, or you misspelled your commit message, or both. Leaves working tree as it was before "reset".

2. Make corrections to working tree files.

3. "reset" copies the old head to `.git/ORIG_HEAD`; redo the commit by starting with its log message. If you do not need to edit the message further, you can give `-C` option instead.

See also the `--amend` option to git-commit.

#### Undo a commit, making it a topic branch

```sh 
$ git branch topic/wip          (1)
$ git reset --hard HEAD~3       (2)
$ git switch topic/wip          (3)
```
1. You have made some commits, but realize they were premature to be in the `master` branch. You want to continue polishing them in a topic branch, so create `topic/wip` branch off of the current HEAD.

2. Rewind the master branch to get rid of those three commits.

3. Switch to `topic/wip` branch and keep working.