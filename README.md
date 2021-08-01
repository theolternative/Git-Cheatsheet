# Git-Cheatsheet
## Basics
Git is a Distributed Version Control System based on **snapshots** (not deltas as other VCs). Each file or directory structure is stored in a database as a 40-byte string checksum calculated via SHA-1 hash. Each file can be in three states: *modified* (you changed the file since the last commit), *staged* (you marked a modified file in your current version to go into your next commit snapshot) or *committed* (the file is stored in your local database and hasn't been modified).
Files can be *untracked* or *tracked* (all files in your last snapshot as well as newly staged files).
Workflow is as follows:
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

## Working with repositories
Command|Description
-------|-----------
`git init`|Initialize your current working directory creating a .git subdirectory
`git clone https://github.com/theolternative/Git-Cheatsheet`|Clone repository in your current directory

In file `.gitignore` you can specify which files are ignored
```
   # ignore all .txt files
  *.txt
  # ignore all files in any directory named node_modules
  node_modules/
  # ignore all .pdf files in the doc/ directory and any of its subdirectories
  doc/**/*.pdf
```

## Common use commands
Command|Description
-------|-----------
`git add <files>`|Mark files as staged ready to be commited
`git rm <files>`|Deletes files from working directory and remove from git
`git mv <oldname> <newname>`|Renames a file
`git commit -m 'Bug fixes'`|Commit files with message 
`git commit -a -m 'Bug fixes'`|Commit all tracked modified files with message 
`git status`|Status of untracked/tracked, modified/staged/committed
`git status --short`|Quick status report
`git diff`|Show differences of modified files not yet staged
`git diff --staged`|Show differences of staged files not yet committed

