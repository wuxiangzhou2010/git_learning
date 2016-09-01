## Git tricks

### modify commit messages
``` shell
git commit --amend -m "your new commit message"
# note: if you have commited to the remote  you can push again by force
git push <remote> <branch> --force
```
### git reset 
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
