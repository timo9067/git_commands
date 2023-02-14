# DESCRIPTION

Manage the set of repositories ("remotes") whose branches you track.

# OPTIONS
-v
--verbose
Be a little more verbose and show remote url after name. 

# COMMANDS

With no arguments, shows a list of existing remotes. Several subcommands are available to perform operations on the remotes.

## `add`

Add a remote named <name> for the repository at <URL>. 

With -f option, git fetch <name> is run immediately after the remote information is set up.

With --tags option, git fetch <name> imports every tag from the remote repository.

With --no-tags option, git fetch <name> does not import tags from the remote repository.

By default, only tags on fetched branches are imported (see git-fetch[1]).

## `rename`

Rename the remote named <old> to <new>. All remote-tracking branches and configuration settings for the remote are updated.

## `remove`

Remove the remote named <name>. All remote-tracking branches and configuration settings for the remote are removed.

## `set-head`

Sets or deletes the default branch (i.e. the target of the symbolic-ref refs/remotes/<name>/HEAD) for the named remote. 

With -d or --delete, the symbolic ref refs/remotes/<name>/HEAD is deleted.

## `set-branches`

Changes the list of branches tracked by the named remote. This can be used to track a subset of the available remote branches after the initial setup for a remote.

## `get-url`

Retrieves the URLs for a remote. Configurations for insteadOf and pushInsteadOf are expanded here. By default, only the first URL is listed.

## `set-url`
Changes URLs for the remote. 

With --push, push URLs are manipulated instead of fetch URLs.
