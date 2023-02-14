# push-commands


git push
---
The "push" command is used to publish new local commits on a remote server.

The source (i.e. which branch the data should be uploaded from) is always the currently checked out HEAD branch.

The target (i.e. which branch the data should be uploaded to) can be specified in the command's options. These options can be omitted, however, if a tracking relationship with a remote branch is set up.

Note that the "push" command can also be used to delete a remote branch.

## Important Options
---

--all
Pushes all local branches.

--tags
Pushes all local tags.

--delete
Deletes the specified remote branch.

-u
Creates an upstream tracking connection and is especially useful when publishing a local branch on a remote for the first time.


## Usage Examples
---
Before using "git push", make sure the correct local branch is checked out. Then, to perform the push, simply specify which remote branch you want to push to:

git checkout develop
git push origin develop
If you are publishing a local branch for the first time on a remote, the "-u" option is helpful. It makes sure that a tracking connection between the local and the newly created remote branch is established:

git push -u origin develop
After having set up such a tracking connection, you can perform future pushes without providing additional options - since the tracking connection provides default values for the push command:

git push
To delete a remote branch, simply use the "--delete" option and specify which branch (on which remote) you want to delete:

git push origin --delete feature/login
