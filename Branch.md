
## The `git` **branch** Command
---
### Description
---

A branch represents an independent line of development. Branches serve as an abstraction for the **edit/stage/commit** process. 

You can think of them as a way to request a brand new working directory, staging area, and project history. New commits are recorded in the history for the current branch, which results in a fork in the history of the project.

The `git branch` command lets you **create, list, rename, and delete branches**. It doesn’t let you switch between branches or put a forked history back together again.

For this reason, `git branch` is tightly integrated with the `git switch` and `git merge` commands.


### Options 
---

- ```-v , -a ```

Adding the "-a" flag will make sure remote branches are also included in the list.

Adding the "-v" flag will make the command more "verbose" and include SHA-1 hashes as well as commit subjects of the latest commits on your branches.


- ```--no-merged```

This helps you understand which changes haven't been integrated into your current working context, yet. Note that you can also request all branches that already have been merged in your current HEAD by using the "--merged" option instead.


- ```-d <branch name> ```

If the specified branch hasn't been fully merged yet, you'll have to use the capital "-D" flag. Be careful with this, though: deleting branches that contain unmerged data shouldn't be done lightly.
If you want to delete a remote branch, add the "-r" flag in addition to "-d".

- ```<new-branch>```

Create a new local branch based on your currently checked out branch. If you also provide a SHA-1 hash of a specific revision, your new branch will use that commit as its starting point.

### Examples
---
You can list all branches (both local and remote), including the SHA-1 hashes and commit subjects that these branches currently point to:
```
$ git branch -a -v
  * master 609d1ee New icons for “teams” page
    feature/login 82a0f21 Add test cases
```
Using the "--no-merged" option, you can find out which of your local branches have not been integrated into your current HEAD branch, yet:
```
$ git branch --no-merged
  feature/accounts
```
In case you want to clean up and delete branches that have already been integrated, you could use "--merged" to find these branches and then delete them using "-d":
```
$ git branch --merged
  feature/login
  feature/newsletter
$ git branch -d feature/login feature/newsletter
```
To create a new branch, simply specify a name - and possibly a starting point, in case you don't want it to start at your current HEAD branch's state:
```
$ git branch feature/logout b84f02e
```
