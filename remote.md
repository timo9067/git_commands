## The "git" **remote** command

### Description
---

Manage the set of repositories ("remotes") whose branches you track.

### Options
---
`-v- -verbose`

Be a little more verbose and show remote url after name. 

### Commands
---

With no arguments, shows a list of existing remotes. Several subcommands are available to perform operations on the remotes.


#### add

Add a remote named <name> for the repository at <URL>. 

- With `-f` option, git fetch <name> is run immediately after the remote information is set up.

- With `--tags` option, git fetch <name> imports every tag from the remote repository.

- With `--no-tags` option, git fetch <name> does not import tags from the remote repository.

#### rename

- Rename the remote named <old> to <new>. All remote-tracking branches and configuration settings for the remote are updated.


#### remove

- Remove the remote named <name>. All remote-tracking branches and configuration settings for the remote are removed.

#### set-head

- Sets or deletes the default branch for the named remote. 

- With `-d` or `--delete`, the symbolic ref is deleted.

#### set-branches

- Changes the list of branches tracked by the named remote. This can be used to track a subset of the available remote branches after the initial setup for a remote.

#### get-url

- Retrieves the URLs for a remote. Configurations for insteadOf and pushInsteadOf are expanded here. By default, only the first URL is listed.

#### set-url
- Changes URLs for the remote. 

- With `--push`, push URLs are manipulated instead of fetch URLs.

### Examples
---
List the remote connections you have to other repositories.
```git
$ git remote
```
Same as the above command, but include the URL of each connection.

```git
$ git remote -v
```
