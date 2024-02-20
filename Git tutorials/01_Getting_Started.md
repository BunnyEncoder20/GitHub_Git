**Latest Version (2.41.0.windows.1) of Git installed (on 13/06/23)**
**NOTE : git and github are different**

---


# Getting Started (Setup) with Git

## Step #1) Configuring the git 

To assign our name : 
```
git config --global user.name "Username" 
```

To assign our email : 
```
$ git config --global user.email "your@email.com"
```

**NOTE:** keep the same email as the one in the `GitHub profile`

To display the Username / Email 
```
git config --global user.name 
git config --global user.email 
```
**Note:** Repo equivalent to kinda folder 

---


## Step #2) Initializing a Git Repository (folder)

**Basics of CLI** 
1. `cd` - change directory - used for changing the path / where you at  (`cd ..` - to go back a folder)
2. `ls` - lists the items in that folder 
3. `pwd` - gives the current path 
4. `mkdir` - creates a folder 
5. `touch file_name1.html file_name2.css file_name3.js` - creates 3 files : file_name1.html, file_name2.css, file_name3.js
6. `rm file_name.html` - deletes the file : file_name.html 

**For Initializing an empty Git Repo :** 
```
git init
```

- Now all of the changes made in this folder will be tracked by the git version control system


**Git Zones**
1. `Untracked zone` - all the files which have been tracked 
2. `Staging zone` - some of the files (maybe excluding the build files / readme files) that are selected for committing and put here
3. `Commit zone`- these are check points sort of for the files / changes made in the Repo

---

## Step #3) Some Basic Git commands 

1. `git status`: tells us which **branch** we're on, the **commits** made, **changes** to be committed and **untracked** changes and files 

2. `git add file_name.html`: shifts the document from _untracked_ to the _staging area_ (for only the file specified.)

3. `git add . `: adds all the files with changes made into the staging zone

4. `git rm --cached file_name.html`: undoes the above command (moves file from staging to untracked zone)

5. `git commit -m "msg here. YES it is compulsory"`: commits all of the files in the staging area 

> **Note:** **-m** is a message flag

6. `git log`: shows details about the commits made, their authors , date and time , msg given during the commit 


> **NOTE:** 
>- In order to make some files not be staged or committed every time, we can make a txt file named **.gitignore** (yes the . needs to be there, it is not the file extension thing) and write all the files names which we wish to be excluded in it.
>- You can also go online to .gitignore file generators


---

## Git file annotations 

- These are what the symbols (Letters) in front of your files means : 

1. **A** - Added (This is a new file that has been added to the repository)

2. **M** - Modified (An existing file has been changed)

3. **D** - Deleted (a file has been deleted)

4. **U** - Untracked (The file is new or has been changed but has not been added to the repository yet)

5. **C** - Conflict (There is a conflict in the file)

6. **R** - Renamed (The file has been renamed)

7. **S** - Submodule (In repository exists another subrepository)

8. **T** - Typechange (The file changed from symlink to regular file, or visa versa)

---

## Git Checkout commands 

1. `git checkout commitID`: is a command in Git used to switch branches or restore files versions. **commitID** refers to the unique identifier of a commit in Git, typically a hash value associated with a specific commit.

2. `git checkout master`: This takes us back to the latest committed version.

---

## Git Branches 

1. `git branch`: shows all the `branches` available in the repo

2. ` git branch branchName`: makes a new `branch` by the name of _branchName_

3. `git checkout branchName`: takes us (`head`) to that branch. (current branch is highlighted in green, preceded by a star)

4. `git checkout -b new_branchName`: creates a new branch "branchName" and takes us onto it 

5. `git push`: pushes all the commits to the **main/master branch** - from local machine to the Online repo (GitHub)


**GitHub recommended code to initialize a repository :**
``` 
echo "# GitHub_Password-Generator" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/BunnyEncoder20/GitHub_Password-Generator.git
git push -u origin main 
```
---

## GitHub integration with desktop git repo 

1. `git init` the folder on your computer 
2. do initial commit
3. `git remote add origin <link_to_github_repo>`: hooks the local folder to the website online repository (folder)
4. `git push -u origin main` - initial commit to the main branch

**Creating a new Branch and Merging it back into Main branch**

5. `git checkout -b new_branch`
6. commit changes to this branch 
7. `git push origin new_branch`: pushes the new branch made onto Github (You can see the various branches in GitHub)
8. **Branch owner** can create a `pull request` (Compare & Pull request button on GitHub -> create)
9. Owner of the `main branch` can go over the files changes (in the "File Changed" Tab in GitHub)
10. Owner of the `main branch` can merge  the branch into the `Main branch` ("Merge Pull Request" button in Github)

**Pulling latest changes from the GitHub repo to your local computer**

11.  git pull origin master - pulling main branch latest changes to the local computer
12.  git pull origin <branchName>

---

# Tips : 

1. When we create empty folder structure for our professional projects, empty folders alone will not be pushed to github. So we add an empty file inside them called `.gitkeep` (similar to `.gitignore`)

2. use `git restore --staged <file>...` to un-stage changes (reverse of `git add .`)

3. to checkout the current remote URL : `git remote -v`

4. to simply remove the remote origin : `git remote remove origin`
   
5. to change the remote URL : `git remote set-url origin <github repo link>`

6. If you accidentally leak secret files (like .env) : https://varunx.hashnode.dev/pushed-env-file-to-github#heading-how-to-fix-this

