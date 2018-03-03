## Git tricks

### modify commit messages
``` shell
git commit --amend -m "your new commit message"
# note: if you have commited to the remote  you can push again by force
git push <remote> <branch> --force
```
### git reset 
```
revert git added(or discard changes in the staging area)
With or without --hard option, any local commits that haven't been pushed will be lost
git reset resets the master branch to what you just fetched. The --hard option changes all the files in your working tree to match the files in origin/master
``` shell 
git reset <some added file >
## reset all added files 
git reset (--all)
git reset --hard original/master
# OR If you are on some other branch
git reset --hard origin/your_branch
```
### git fetch
downloads the latest from remote without trying to merge or rebase anything.
save what you have change to the new-branch and reset the master
``` shell 
git checkout master 
git branch new-branch
git fetch --all
git reset --hard original/master
```
### git config
``` shell
git config --global user.name "xxx" 
git config --global user.email "xxx@gmail.com"
# show git config 
git config --list
```
### discard modification  in the workspace
``` shell
git checkout -- file.c
```
### delete untracked files and directories
``` shell
git clean -df
```
### a shallow clone (meaning not cloning the all history), this will speed up the clone
``` shell 
git clone --depth 1 <repository>
# if you want to see more logs, use git pull or git pull --unshallow 
git pull --depth=10
git pull --unshallow
```
### remove files saying “old mode 100755 new mode 100644” from unstaged changes in Git
```
git config core.filemode false
```
### clone from svn repo 
```
git svn clone URL
git svn clone --stdlayout --authors-file=authors.txt https://svn.atlassian.com/Confluence ConfluenceAsGit
```
### change the url of the repo
```
git remote -v
git remote set-url origin https://github.com/USERNAME/OTHERREPOSITORY.git
```

### change the commit author and message

```
git rebase -i <earliercommit>
# change the pick to edit, save 
git commit --amend --author="Author Name <email@address.com>"
```
- [link](https://stackoverflow.com/questions/3042437/change-commit-author-at-one-specific-commit)
- [official link](https://help.github.com/articles/changing-a-commit-message/)

### 
```
git config --global core.autocrlf true
git config core.fileMode false
```
