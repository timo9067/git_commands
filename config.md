# <u>**Git Config commands**</u>

## **git config --local**

When no configuration option is passed git config writes to a local level, by default.The repository of the .git directory has a file that stores local configuration values.
## **git config --local --list**

## **git config --global**

The application of the global level configuration includes the operating system user. Global configuration values can be found in a file placed in a user's home directory.

## **git config --global --list**

## **git config --global credential.helper cache**


## **git config --global user.name "name"**
## **git config --global user.email "email address"**

The global level is used so as to set the value for the current operating system user.

## **git config --system**

The System-level configuration includes all users on an operating system and all repositories. System-level configuration file is located in a git config file of the system root path. 