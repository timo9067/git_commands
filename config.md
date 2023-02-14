
## <u> Git Config commands </u>

### Description
---

The git config command is a convenience function that is used to set Git configuration values on a global or local project level. These configuration levels correspond to . gitconfig text files. Executing git config will modify a configuration text file.

### Options

---
- `git config --local`

When no configuration option is passed git config writes to a local level, by default.The repository of the .git directory has a file that stores local configuration values.

---

- `git config --local --list`
- `git config --global --list`

The git config list command will show all Git config properties throughout all of the variously scoped Git files.

---

- `git config --global`

The application of the global level configuration includes the operating system user. Global configuration values can be found in a file placed in a user's home directory.

---
- `git config --global credential.helper cache`

This command caches credentials in memory for use by future Git programs.

---

- `git config --global user.name "name"`
- `git config --global user.email "email address"`

The global level is used so as to set the value for the current operating system user. These commands help with setting your user name and email.

---
- `git config --system`

The System-level configuration includes all users on an operating system and all repositories. System-level configuration file is located in a git config file of the system root path.

---
