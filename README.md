# Git Cheatsheet
## Basics
Git is a Distributed Version Control System based on **snapshots** (not deltas as other VCs). Each file or directory structure is stored in a database as a 40-byte string checksum calculated via SHA-1 hash. Each file can be in three states: *modified* (you changed the file since the last commit), *staged* (you marked a modified file in your current version to go into your next commit snapshot) or *committed* (the file is stored in your local database and hasn't been modified).
Files can be *untracked* or *tracked* (all files in your last snapshot as well as newly staged files).
Workflow is as follows:
- You modify files in your wokring tree
- You mark files as staged ready to be committed
- You commit staged files
- 
You can create **branches** in order to test experimental features or developt hot fixes:
- You create a new branch and switch to it
- You commit changes
- You switch to master branch
- You merge changes to master branch
- 
Git checks *last common branch* in order to merge changes. Suppose you create branch `NewFeatures` make changes and commit but don't merge; then you create branch `HotFix` make changes, commit and merge to `master` branch. Now if you try to merge `NewFeatures` branch to `master`, there are two cases:
1) Merge **succeeds** since no files changed in `HotFix` branch have been changed in `NewFeatures` branch (no conflics).
2) Merge **fails** since one or more files changed in `HotFix` branch have also been changed in `NewFeatures` branch. Git can't determine which version is worth keeping.
In the latter case manually edit each file marked as *unmerged* (Git adds markers in each file showing which parts differ), add to stage and commit.

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
By default Git identifies remote repositoru as `origin`

Command|Description
-------|-----------
`git init`|Initialize your current working directory creating a .git subdirectory
`git clone https://github.com/theolternative/Git-Cheatsheet`|Clone repository in your current directory
`git log`|See log of changes
`git log --oneline --decorate --graph --all`|Quick log with all branches
`git remote -v`|List configured remote servers
`git fetch <remote>`|Fetch data from remote since last fetched BUT doesn't merge 
`git pull <remote>`|Fetch data from remote since last fetched AND does merge to current working directory
`git push <remote> <branch>`|Push data to remote ONLY if remote branch has not changed since last fetch
`git push <remote> --delete <branch>`|Delete branch name in remote
`git push --set-upstream <remote> <newbranch>`|Push branch to remote
`git checkout <branch>`|Create a local branch from remote <branch>

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
`git restore --staged <files>`Mark staged files as unstaged
`git restore <files>`Discard modified files in working directory and replace with last staged or committed
`git rm <files>`|Deletes files from working directory and remove from git
`git mv <oldname> <newname>`|Renames a file
`git commit -m 'Bug fixes'`|Commit files with message 
`git commit -a -m 'Bug fixes'`|Commit all tracked modified files with message 
`git commit -amend'`|Overwrites last snapshot with staged changes 
`git tag -a v1.0 -m "Initial release"`|Add a tag to current commit
`git tag -a v1.0 -m "Initial release" <commit checksum>`|Add a tag to commit with specified checksum
`git tag -d v1.0`|Delete a tag
`git status`|Status of untracked/tracked, modified/staged/committed
`git status --short`|Quick status report
`git diff`|Show differences of modified files not yet staged
`git diff --staged`|Show differences of staged files not yet committed
`git show v1.0`|Show tag

## Branching
Command|Description
-------|-----------
`git switch -c <newbranch>`|Create new branch and switch to it
`git switch -c <newbranch> <existingbranch>`|Create new branch from existing branch and switch to it
`git switch <name>`|Switch to an existing branch
`git branch -d <name>`|Delete branch
`git branch -v`|Check last commit on each branch
`git branch -move <oldname> <newname>`|Rename branch
`git merge <branchname>`|Merge changes in branchame to current branch
