# Git-Cheatsheet
## Basics
Git is a Distributed Version Control System based on **snapshots** (not deltas as other VCs). Each file or directory structure is stored in a database as a 40-byte string checksum calculated via SHA-1 hash. Each file can be in three states: *modified* (you changed the file since the last commit), *staged* (you marked a modified file in your current version to go into your next commit snapshot) or *committed* (the file is stored in your local database and hasn't been modified). Workflow is as follows:
- You modify files in your wokring tree
- You mark files as staged ready to be committed
- You commit staged files

## Get help
Command|Description
-------|-----------
`git help <verb>`|Verbose description
`git <verb> -h`|Quick description

## First time setup
Setup your *username* and *email*. 
Configuration files can be **global**, **user-specific**, **repository-specific**. Each level overrides values in the previous level. 

Command|Description
-------|-----------
`git config --list --show-origin`|Check config files locations
`git config --list`|Check configuration settings
`git config user.name`|Check specific setting
`git config --global user.name "Theo Reds"`|Set global username
`git config --global user.email "theo@example.com"`|Set global user email

## Initializing a repository in an existing directory
```
git config --global user.name "Theo Reds"
git config --global user.name "theo@example.com"
```
