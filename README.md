# git-setup

![](https://img.shields.io/badge/git-git%20version%202.36.0.windows.1-red)

This is just my personal setup for `GIT` https://git-scm.com/

## Git Global Configuration

To list down global configuration, use the following command below:

```
git config --global -l
```

```
user.name=lightzane
user.email=lightzane@email.com
credential.helper=ghp_A12BC3de456FGH0ijKLmNopQRsTuVW7xy8Z9
core.editor=code --wait
alias.lg=log --pretty=format:'%C(auto) %h %d %s (%C(magenta)%an%C(auto)) %ar'
alias.lgg=log --graph --pretty=format:'%C(auto) %h %d %s (%C(magenta)%an%C(auto)) %ar'
alias.cloud=!f() { git add . && git commit -m "$@" && git push; }; f
alias.save=!f() { git add . && git commit -m "$@"; }; f
```

> Can also use the following command: `git config --global -e` to view list and edit in Editor (`code.editor`)

## Usage

```
git cloud "initial commit"
```

## Setup Git Global Configurations

```
git config --global alias.lg "log --pretty=format:'%C(auto) %h %d %s (%C(magenta)%an%C(auto)) %ar'"
```

```
git config --global alias.lgg "log --graph --pretty=format:'%C(auto) %h %d %s (%C(magenta)%an%C(auto)) %ar'"
```

```
git config --global alias.cloud "!f() { git add . && git commit -m \"$@\" && git push; }; f"
```

```
git config --global alias.save "!f() { git add . && git commit -m \"$@\"; }; f"
```

## Pretty Formats

`--pretty=format:'...'`

| #          | Description                                                                            |
| ---------- | -------------------------------------------------------------------------------------- |
| `%C(auto)` | will turn on auto coloring on the next placeholders until the color is switched again. |
| `%h`       | abbreviated commit has (`%H` for full commit hash)                                     |
| `%d`       | ref names (e.g. `(HEAD -> origin/main, main)`)                                         |
| `%s`       | subject (commit message)                                                               |
| `%C(...)`  | font color specification                                                               |
| `%an`      | author name                                                                            |
| `%ar`      | author date in relative form e.g. 5mins ago (see also: `%ah` and `%ad`)                |

## Removing config

`git config --global --unset <variable_name>`

## Git common usages

| command                                  | description                                                                  |
| ---------------------------------------- | ---------------------------------------------------------------------------- |
| `git add .`                              | adds all untracked, modified, deleted files and folders to stage for commit  |
| `git commit -m "msg"`                    | commits all files in the staged changes                                      |
| `git push`                               | push commits to the cloud repository (remote/origin)                         |
| `git fetch`                              | checks if there are new updates available from the cloud/bare repository     |
| `git pull`                               | downloads the latest changes from the remote branch to local branch          |
| `git pull --rebase`                      | (same as above) and additionally moving your commits on top of their commits |
| `git pull origin <branch_name>`          | pull from a other branch                                                     |
| `git pull origin <branch_name> --rebase` | (same as above) and additionally moving your commits on top of their commits |
| `git checkout <branch_name>`             | switch to another branch                                                     |
| `git checkout -b <branch_name>`          | create a new branch from the active branch                                   |
| `git checkout --orphan <branch_name>`    | create new branch from active branch without git history                     |

## Git local repository management

| command                          | description                                              |
| -------------------------------- | -------------------------------------------------------- |
| `git status`                     | check the status of the current branch                   |
| `git branch -avv`                | displays all the branches with remote references         |
| `git remote add origin <url>`    | add origin for your **non-bare** local `.git` repository |
| `git remote remove origin <url>` | removes origin from local                                |

## Other Git commands

| command                                  | description                                                                                  |
| ---------------------------------------- | -------------------------------------------------------------------------------------------- |
| `git stash`                              | add uncommited changes to stash (good to save changes if not ready to commit)                |
| `git stash -m "msg"`                     | store uncommited changes with a description of the stash                                     |
| `git stash pop`                          | applies and delete the change in stash (applies the latest stash if more than 1 in the list) |
| `git init`                               | initialize a common directory to a local git repository                                      |
| `git init --bare <repo_name>`            | creates a **bare** local `.git` repository (local cloud)                                     |
| `gitk`                                   | display git visual                                                                           |
| `git reset --soft HEAD~n`                | resets back to `n`th previous commits and puts the changes to staged                         |
| `git reset --soft <SHA>`                 | resets back to the last commit after the specified `SHA` or branch name                      |
| `git config --system init.defaultbranch` | default is `main` branch                                                                     |

## Advanced Git commands

**Careful using this**

| command                              | description                                           |
| ------------------------------------ | ----------------------------------------------------- |
| `git rebase -i HEAD~n`               | pick commits back to `n`th previous commits           |
| `git rebase -i <SHA or branch_name>` | pick commits after the specified `SHA` or branch name |

> You might need to change git config `core.editor=code --wait` or other editor to make editing much easier
