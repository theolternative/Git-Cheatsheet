# Git-Cheatsheet
## Get help
`git help <verb>`

## First time setup
### Configuration files
Configuration files can be **global**, **user-specific**, **repository-specific**. Each level overrides values in the previous level. 

Command|Description
-------|-----------
`git config --list --show-origin`|Check config files locations
`git config --list`|Check configuration settings
`git config user.name`|Check specific setting
`git config --global user.name "Theo Reds"`|Set global username
`git config --global user.email "theo@example.com"`|Set global user email

### Basic settings
```
git config --global user.name "Theo Reds"
git config --global user.name "theo@example.com"
```
