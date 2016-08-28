## Git tricks

### modify commit messages
``` shell
git commit --amend -m "your new commit message"
```
note: if you have commited to the remote  you can push again by force by
``` shell
git push <remote> <branch> --force
```
### revert git add 
``` shell 
git reset <some added file >
## reset all added files 
git reset 
```
