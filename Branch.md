# The `git` **branch** Command:

A branch represents an independent line of development. Branches serve as an abstraction for the **edit/stage/commit** process. 

You can think of them as a way to request a brand new working directory, staging area, and project history. New commits are recorded in the history for the current branch, which results in a fork in the history of the project.

The `git branch` command lets you **create, list, rename, and delete branches**. It doesn’t let you switch between branches or put a forked history back together again.

For this reason, `git branch` is tightly integrated with the `git switch` and `git merge` commands.

## Options for this command
----
```
-v , -a : Provides more information about all your branches.
```
```
--merged : Returns all branches that have been merged into your 
            current HEAD branch.
```
```
--no-merged : Returns all branches that have not been merged into 
                your current HEAD branch.
```
```
-d <branch name> : Deletes a specified branch.
```
```
-D <branch name> : Force delete a specified branch, even if it   
                    has unmerged changes.
```
```
<new-branch> : Create a new local branch 
```
