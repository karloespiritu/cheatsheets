---
layout: page
title: Git
permalink: /git/
---

Here are some of the Git commands that I often use.

```bash
git config --list
```
Change origin URL

```bash
git remote set-url origin http//github.com/repo.git
```
Add remote repo

```bash
git remote add remote-name https://github.com/user/repo.git
```

Syncing a fork

```bash
//Fetch the branches and their respective commits from the upstream repository. Commits to master will be stored in a local branch, upstream/master
git fetch upstream
git checkout master
git merge upstream/master
```

##Commits

Unstage a file for commit

```bash
git reset <file>
```

Combining commits

```bash
//Interactive rebasing of last 4 commits
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

Temporarily stash changes, apply later

```bash
//Stash current changes
git stash

#Do some new changes

//Apply stashed changes
git stash apply
```


##Manage Branches

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
git push origin :the_remote_branch
```

