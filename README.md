# Git-Cheatsheet
## First time setup
### Configuration files
Configuration files can be **global**, **user-specific**, **repository-specific**. Each level overrides values in the previous level. Check config files locations with command

`$ git config --list --show-origin`

### Basic settings
```
git config --global user.name "Theo Reds"
git config --global user.name "theo@example.com"
```
