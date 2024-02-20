# Fireship Git Tips
---

## 1. Combining the `git add` and `git commit` commands
- This can be done by going straight to `git commit` and using the **`-am`** flag to automatically do a `git add .`
```git 
git commit -am "commit message"
```
---

## 2 Making alias 

- `git config` has a feature where we can define our own alias which can then run a specified command : 
- **Eg:** we want to shorten the `git commit -am "noice"` command to just 2 letters : 
```git 
git config --global alias.ac "commit -am"
```
- This will replace the words `ac` with `commit -am` on execution , so now we can run same command as :
```git 
git ac "commit message"     
```
- which will function the same as `git commit -am "commit message"`

---

## `--amend` flag

- if there was a mistake in the last commit message , we can correct that using the `--amend` flag in a commit command :
```git 
git commit --amend -m "corrected commit message"
```
- if you forgot to add some files in the last commit, you can stage them as well into the previous commit as well with the `--amend` flag:
```git
git add .
git commit --amend --no-edit
```
- if we do not want to update the previous commit message, we use the `--no-edit` flag as seen above.
> **NOTE:** 
>- this only works if you have not pushed the code to the remote repository
>- if you want to _live dangerously_ , you can use the `--force` flag to push your version of the code onto the remote repo. However if there are commits on the remote repo which you do not have, they will be lost.

---

## 3. `git revert` command

- If you push code to the remote repo but then realize that it was garbage and should have never been pushed , you can use the 
- `git revert` command to revert the last commit with a new commit 
```git
git revert commitID
```
- it doesn't remove the previous commit, but it creates a new commit which is essential reverting back to the previous state (before the bad commit)
- This is often better than trying to undo everything that the bad commit ruined 

---

## 4. Codespaces

- `GitHub` CodeSpaces can give you a lite browser-based version of VScode which you can use to make edits in the repo, submit PRs, etc 
- If you want to use the terminal, you'll have to make a codespace cloud env 

---

## 5. `stash` command

- When you have made some changes to your work, but you can't commit it yet cause it breaks everything else?
- `git stash` removes all the changes from your current working directory and saves them for later use without committing them.
- `git stash pop` will add those stashed changes back into the directory.
```
git stash
git stash pop
```
- if you use the feature of stash a  lot, you can name your stashes:
```git 
git stash save unstable_code_v1
```
- you can them use the `git stash list` command to see all your stashes :
```git 
git stash list
stash@{0}: On master: unstable_code_v1
```
- and use the `git stash apply index` command to apply a specific stash (index is a number) :
```git 
git stash apply 0
```

---

## 6. Renaming Main branch

- historical the git's main branch was named `master` , but it is now `main` (from 2020)
- you can rename the main branch by:
```git 
git branch -M muncho
```

---

## 7. `log` Command 

- this command gets harder and harder to read when your project grows in size (multiple commits done)
- to make the output easier to read, and more informative at the same time, we can add the 
  - `--oneline` flag
  - `graph` flag
  - `--decorate` flag
- **Eg:**
```git 
git log --oneline --graph --decorate
```
---

## 8. `reset` Command

- if you made some changes in a code base after pulling a stable version from the remote repo and now the code is not working (for some reason)
- We can go back to the latest version of the remote repo using the `git reset` command like so:
    1. fetch  the latest changes 
    2. hard reset the local code (**be careful, cause all of the changes made to the local code will be lost**)
```git 
git fetch origin
git reset -hard origin/main
git clean -df
```
- `git clean` removes an remaining files or build files still left after the reset