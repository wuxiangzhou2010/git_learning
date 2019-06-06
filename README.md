# git_learning

This is git learning note, may be helpful to you.

## modify commit messages

``` shell
git commit --amend -m "your new commit message"
# note: if you have commited to the remote  you can push again by force
git push <remote> <branch> --force
```

## git reset

revert git added(or discard changes in the staging area)
With or without --hard option, any local commits that haven't been pushed will be lost
git reset resets the master branch to what you just fetched. The --hard option changes all the files in your working tree to match the files in origin/master

``` shell
git reset <some added file >

# reset all added files
git reset (--all)
# reset the file committed in local repo
git reset --soft HEAD^

git reset --hard original/master
# OR If you are on some other branch
git reset --hard origin/your_branch
```

## git fetch

downloads the latest from remote without trying to merge or rebase anything.
save what you have change to the new-branch and reset the master

``` shell
git checkout master 
git branch new-branch
git fetch --all
git reset --hard original/master
```

## git config

``` shell
git config --global user.name "xxx" 
git config --global user.email "xxx@gmail.com"
# show git config 
git config --list
```

## discard modification  in the workspace

``` shell
git checkout -- file.c
```

## delete untracked files and directories

``` shell
git clean -df
```

## a shallow clone (meaning not cloning the all history), this will speed up the clone

``` shell 
git clone --depth 1 <repository>
# if you want to see more logs, use git pull or git pull --unshallow 
git pull --depth=10
git pull --unshallow
```

## remove files saying “old mode 100755 new mode 100644” from unstaged changes in Git

``` sh
git config core.filemode false
```

## clone from svn repo 

``` sh
git svn clone URL
git svn clone --stdlayout --authors-file=authors.txt https://svn.atlassian.com/Confluence ConfluenceAsGit
```

## change the url of the repo

``` sh
git remote -v
git remote set-url origin https://github.com/USERNAME/OTHERREPOSITORY.git
```

## [proxy through socks5](https://stackoverflow.com/questions/15227130/using-a-socks-proxy-with-git-for-the-http-transport)

```sh
git config --global http.proxy socks5h://192.168.1.123:4567

http_proxy=socks5://127.0.0.1:4567 go get github.com/mattn/go-sqlite3

# unset proxy

git config --global --unset http.proxy
```

## change the commit author and message

``` sh
git rebase -i <earliercommit>
# change the pick to edit, save 
git commit --amend --author="Author Name <email@address.com>"
```

- [link](https://stackoverflow.com/questions/3042437/change-commit-author-at-one-specific-commit)
- [official link](https://help.github.com/articles/changing-a-commit-message/)

## file mode and line endings

``` sh
git config core.fileMode false

# On Windows:
git config --global core.autocrlf true

# On Linux:
git config --global core.autocrlf input
```

## [convert svn  to git](http://john.albin.net/git/convert-subversion-to-git)

## Save credential

``` sh
git config credential.helper store
```

## Sync with origin branch in fork branch

``` sh
# In your local clone of your forked repository, you can add the original GitHub repository as a "remote". ("Remotes" are like nicknames for the URLs of repositories - origin is one, for example.) Then you can fetch all the branches from that upstream repository, and rebase your work to continue working on the upstream version. In terms of commands that might look like:

# Add the remote, call it "upstream":

git remote add upstream https://github.com/i5ting/How-to-learn-node-correctly.git

# Fetch all the branches of that remote into remote-tracking branches,
# such as upstream/master:

git fetch upstream

# Make sure that you're on your master branch:

git checkout master

# Rewrite your master branch so that any commits of yours that
# aren't already in upstream/master are replayed on top of that
# other branch:

git rebase upstream/master
git push -f origin master
```

## [Sync fork branch same as upstream](https://gist.github.com/glennblock/1974465)

``` sh
git remote add upstream https://github.com/some_user/some_repo
git fetch upstream
git checkout master
git reset --hard upstream/master
git push origin master --force
```

## rest remote to a commit(not recommended)

```sh
 git reset --hard <commit-hash>
 git push -f origin master
```

## git merge and git rebase

- `merge` will keep the same history
- `rebase` will  base feature branch commit on master in below case

```sh
# merge
git checkout feature1
git merge master

# rebase
git checkout feature1
git rebase master

# abort rebease
git rebase --abort

```
