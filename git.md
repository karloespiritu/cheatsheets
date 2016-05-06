---
layout: page
title: Git
permalink: /git/
---

Here are some of the Git commands that I often use.

## Basic

Display local repo config settings

```bash
git config --list
```

Show remote repository URL

```bash
git config --get remote.origin.url
# or
git remote show origin
```

Change origin URL

```bash
git remote set-url origin http//github.com/repo.git
```

Add remote repo

```bash
git remote add remote-name https://github.com/user/repo.git
```

Check remote repository URL of current repo

```bash
git config --get remote.origin.url
```

Syncing a fork

```bash
//Fetch the branches and their respective commits from the upstream repository. Commits to master will be stored in a local branch, upstream/master
git fetch upstream
git checkout master
git merge upstream/master
```

## Refactor filenames

```bash
// Deletes file from working directory and stages the deletion
git rm <filename>

// Removes file from version control but preserves file locally
git rm --cached <filename>

// Changes file name and prepares it for commit
git mv <filename-orig> <filename-renamed>

```

## Commits

Unstage a file for commit

```bash
git reset <file>
```

Combining commits

```bash
//Interactive rebasing of last 3 commits
git rebase -i HEAD~3

//Tells Git to combine all 3 commits into the 1st commit
pick 01d112s New header design
squash 63423aa Added search bar
squash ebfd157 Updated header icon
```

Change last commit message

```bash
git commit --amend -m "New commit message"
```

Discard all local changes

```bash
git reset --hard
```

Undo last commit & redo

```bash
git commit ...                (1)
git reset --soft HEAD~1       (2)
<< edit files as necessary >> (3)
git add ....                  (4)
git commit -c ORIG_HEAD       (5)
```

## Stash

Temporarily stash changes, apply later

```bash
// Stash current changes
git stash

//List all stashed changesets
git stash list

# Do some new changes

// Apply stashed changes
git stash apply
```


## Manage Branches

Reset local repo to match remote repo

```bash
git fetch origin
git reset --hard origin/master
```

Pull latest changes from a remote repo

```bash
git fetch
git pull
```

Delete a local branch

```bash
git branch -d <branch-name>
```

Delete a remote branch

```bash
git push origin :remote_branch
```
