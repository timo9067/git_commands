
# DESCRIPTION #
       Updates files in the working tree to match the version in the index or the
       specified tree. If no pathspec was given, git checkout will also update HEAD to
       set the specified branch as the current branch.
## git checkout [<branch>] ##
        git checkout [<branch>] 
           To prepare for working on <branch>, switch to it by updating the index and the
           files in the working tree, and by pointing HEAD at the branch. Local
           modifications to the files in the working tree are kept, so that they can be
           committed to the <branch>.

           If <branch> is not found but there does exist a tracking branch in exactly one
           remote (call it <remote>) with a matching name and --no-guess is not
           specified, treat as equivalent to

               $ git checkout -b <branch> --track <remote>/<branch>

           You could omit <branch>, in which case the command degenerates to "check out
           the current branch", which is a glorified no-op with rather expensive
           side-effects to show only the tracking information, if exists, for the current
           branch.
## git checkout -b|-B <new_branch> [<start point>] ##
    
           Specifying -b causes a new branch to be created as if git-branch(1) were
           called and then checked out. In this case you can use the --track or
           --no-track options, which will be passed to git branch. As a convenience,
           --track without -b implies branch creation; see the description of --track
           below.

           If -B is given, <new_branch> is created if it doesn’t exist; otherwise, it is
           reset. This is the transactional equivalent of

               $ git branch -f <branch> [<start point>]
               $ git checkout <branch>
               
> that is to say, the branch is not reset/created unless "git checkout" is
           successful.

           