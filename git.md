# Richard's Git cheat sheet

Metasyntactic variables are shown using `[brackets]`. These are placeholders to
be replaced with a real value.

## Configuring Git

```
git config --global user.name "Richard Cook"
git config --global user.email "rcook@rcook.org"
```

You can omit `--global` to configure only the current repository.

## Creating repos

```
git init [project-name]
```

```
git clone [url]
```

## Basics

* List all new or modified files to be committed
```
git status
```
* Show differences not yet staged
```
git diff
```
* Show staged differences to be committed
```
git diff --staged
```
* Unstage file while preserving its contents
```
git reset [path]
```
* Commit snapshot in version history
```
git commit -m "[message]"
```
* Replay a branch on top of another
```
git checkout [my-branch]
git rebase [other-branch]
```
* Steal commit from other branch
```
git cherry-pick [commit-hash]
```
* Blow away your HEAD commit
```
git reset --hard HEAD^
```
* Search source code
```
git grep [search-term]
```

## Working with branches

* List all local branches
```
git branch
```
* List all local branches and all untracked branches
```
git branch -a
```
* Switch to branch and update working directory
```
git checkout [branch-name]
```

## Working with remotes

* List all remotes with associated URLs
```
git remote -v
```
* Change `origin` to point to a Git/SSH-protocol URL
```
git remote set-url origin git@github.com:rcook/repo.git
```
* Add new `gitlab` remote to point to repo mirror on GitLab
```
git remote add gitlab git@gitlab.com:rcook/repo.git
```
* Show history on another branch
```
git log -b [branch-name]
```

## Rebasing/merging tasks

* Start interactive rebase at on top of given commit
```
git rebase -i [commit]
```
* Abort rebase
```
git rebase --abort
```
* Take your version of a file
```
git checkout --ours
```
* Take other version of a file
```
git checkout --theirs
```

## Advanced tasks

### Determine commit at which two branches diverge

```
git merge-base [branch-name0] [branch-name1]
```

### Show files in commit

```
git diff-tree --no-commit-id --name-only -r [commit-id]
```

### List commits on one branch but not another

```
git log [branch-name0] ^[branch-name1] --no-merges
```

### Find out which commit deleted a file

```
git log -1 -- [path]
```

### Amend previous commit with current staged changes

```
git commit --amend -CHEAD
```

### Fix line endings in range of commits

```
$ cat $HOME/fix-line-endings
#!/bin/bash
FILES=$(git diff-tree --no-commit-id --name-only -r $GIT_COMMIT)
for i in $FILES
do
  dos2unix $i
done
$ git filter-branch --tree-filter '$HOME/fix-line-endings' -- [start-commit]..
```

## Feature branches

### Basic feature workflow

```
git checkout -b [feature-branch-name]
git status
# Red means file is either changed or not tracked
git add [new-source-file]
git status
# Green means it has been added and is unchanged since you added it
git commit -m [message]
git push -u origin [feature-branch-name]
# Pushes to remote and sets the upstream, so in the future you only need to type "git push"
git branch -vv
# Shows the upstream branches for all local branches
```

### Getting your work into `master`

```
git checkout master
git pull --rebase
git checkout [feature-branch-name]
git rebase master
git checkout master
git merge [feature-branch-name]
git push
```

## Working with Git submodules

### Pull submodules

```
git submodule update --init
```

### Sync submodules

```
git submodule update
```

## Rewriting author/comitter e-mail addresses

```bash
#!/bin/bash
git filter-branch --commit-filter \
'if [ "$GIT_AUTHOR_NAME" = "Richard Cook" ]; then \
export GIT_AUTHOR_NAME="Richard Cook";\
export GIT_AUTHOR_EMAIL=rcook@rcook.org;\
export GIT_COMMITTER_NAME="Richard Cook";\
export GIT_COMMITTER_EMAIL=rcook@rcook.org;\
fi;\
git commit-tree "$@"'
```
