# Table of Contents

<h6>  

| Topic                     | Link                                               |
|---------------------------|----------------------------------------------------|
| Git Add Command Guide     | [Git Add Command Guide](#git-add-command-guide)    |
| GitHub Tech step by step  | [GitHub Tech step by step](#github-tech-step-by-step) |
| Git & GitHub Basic Commands | [Git & GitHub Basic Commands](#git--github-basic-commands) |
</h6>

<br> 

# GitHub Tech step by step

## 🚀 PART 1: SETUP
✅ Step 1: Install Git : <a href=" Windows/macOS/Linux: Download from: https://git-scm.com/">link</a>
<br>
✅ Step 2: Configure Git
```bash
git config --global user.name "AN Mamun"
git config --global user.email "anmamun0@gmail.com"
```
Check your config:

```bash 
git config --list
```

## 📁 PART 2: START A PROJECT
✅ Step 3: Initialize a Git Repository

```bash 
mkdir my-project
cd my-project
git init
```
###### 🎯 Creates a .git folder to track changes.



## 📄 PART 3: TRACK FILES

✅ Step 4: Create a file
```bash 
echo "# My Project" > README.md
```
✅ Step 5: Check the status
```bash 
git status
```
###### Shows changes, untracked files, etc.
 
✅ Step 6: Stage files 
##### Command	Description
```bash
git add file.txt        # Add one file
git add .               # Add all changes in current directory
git add -A              # Add all changes (new, modified, deleted)
git add -u              # Add only modified & deleted
```

✅ Step 7: Commit the changes
```bash 
git commit -m "Initial commit"
Commits the current snapshot.
```


## 🔁 PART 4: WORKING WITH HISTORY
###### Command	Description
```bash
git log                 # Show commit history
git show <commit>       # See details of a specific commit
git diff                # See unstaged changes
git diff --staged       # See staged changes
git reset               # Unstage file
git reset --hard        # Reset everything (use with caution)
```


## 🔙 PART 5: UNDO CHANGES
Command	Action

```bash
git add file.txt        # Add one file
git add .               # Add all changes in current directory
git add -A              # Add all changes (new, modified, deleted)
git add -u              # Add only modified & deleted
```


## 🔄 PART 7: CLONE / PULL / PUSH
Command	Description
 
```bash
git clone <repo>   # Clone repo from GitHub
git pull           # Pull latest code from GitHub
git push           # Push code to GitHub
```


## 🌿 PART 8: BRANCHING
Command	Description
 
```bash
git branch              # List branches
git branch new-feature  # Create new branch
git checkout new-feature # Switch to branch
git checkout -b new-feature # Create + switch to new branch
git merge branch-name   # Merge branches
git branch -d branch-name # Delete a branch
```


## 🤝 PART 9: COLLABORATION

✅ Fork + Clone: Fork repo on GitHub
<br>
Clone it: 

```bash 
git clone https://github.com/username/forked-repo.git
```

✅ Make changes, then push:

```bash 
git add .
git commit -m "Fixed issue"
git push origin main
```
Then create a Pull Request (PR) on GitHub.




## 🛠 PART 10: OTHER USEFUL COMMANDS
Command	Use
 
```bash
git stash          # Save changes temporarily
git stash pop      # Restore stashed changes
git rm file.txt    # Delete and stage
git mv old.txt new.txt  # Rename file
git clean -fd      # Remove untracked files/folders
```
    
---


<br>
<br>
<br>
<br>
<br>


# Git Add Command Guide


```bash 
git add .
git add *
git add --all
git add -A
```

### ✅ 1. `git add .` → Add current directory only  
Adds all tracked and untracked files in the current folder and subfolders, **except deleted files in parent directories**.

- You're inside your project folder.  
- You only want to add files from the current directory downward.

---

### ✅ 2. `git add *` → Add non-hidden files only  
Adds non-hidden files (files **not starting with .**), and won't add files in subdirectories by default unless wildcards are expanded.

- You want to add only visible files.  
- You don’t need to include dotfiles (e.g., `.env`, `.gitignore`).

⚠️ This depends on your shell. It won't add files starting with `.` unless you configure your shell or use `.*`.

---

### ✅ 3. `git add --all` → Add everything (including deletions)  
Stages:  
- All new files  
- All modified files  
- All deleted files

Use when you want to stage everything, including file deletions.  
Best for complete commits (good practice before committing).

---

### ✅ 4. `git add -A` → Exactly the same as `--all`  
Shorthand for `--all`.  

- 📌 Same behavior, different syntax.

---

### ✅ 5. `git add -u` → Add only tracked files  
Stages only **modified** and **deleted** files that are already tracked.  
Does **not** add new untracked files.

- Use when you updated or deleted files already tracked.  
- You don’t want to add new files yet.



<br>
<br>
<br>
<br>
<br>



 

# Git & GitHub Basic Commands

A quick reference table with essential Git commands, explanations, and examples.

---

## Git Commands Table

<h6>
   
| Command               | What It Does                        | Example                                  | Explanation                              |
|-----------------------|-----------------------------------|------------------------------------------|----------------------------------------|
| `git init`            | Create a new Git repo              | `git init`                               | Initialize a new Git repo in current folder |
| `git status`          | Show current repo status           | `git status`                             | Lists tracked/untracked files and changes |
| `git add <file>`      | Stage changes (one or more files) | `git add README.md`                      | Adds `README.md` to staging area        |
| `git add .`           | Stage all changes in current dir  | `git add .`                             | Adds all files in current folder        |
| `git commit -m "msg"` | Save staged changes as a commit   | `git commit -m "Initial commit"`        | Commits with message                    |
| `git log`             | Show commit history                | `git log`                               | Lists commits with details               |
| `git diff`            | Show unstaged changes              | `git diff`                              | Shows what has changed but not staged   |
| `git diff --staged`   | Show staged changes                | `git diff --staged`                     | Shows changes ready to commit            |
| `git reset HEAD <file>`| Unstage a file                    | `git reset HEAD README.md`              | Removes `README.md` from staging        |
| `git checkout -- <file>`| Discard changes in file          | `git checkout -- README.md`             | Restores `README.md` to last commit     |
| `git remote add origin <url>`| Add remote repo             | `git remote add origin https://github.com/user/repo.git` | Connect local to GitHub repo             |
| `git push -u origin main`| Push branch to remote           | `git push -u origin main`                | Push commits to GitHub on main branch   |
| `git pull`            | Fetch and merge changes from remote| `git pull`                             | Update local with remote changes        |
| `git clone <url>`     | Download repo from remote          | `git clone https://github.com/user/repo.git` | Copy remote repo to local machine       |
| `git branch`          | List branches                     | `git branch`                            | Shows all branches                       |
| `git branch <name>`   | Create a new branch               | `git branch feature1`                   | Creates a branch called `feature1`      |
| `git checkout <name>` | Switch branches                  | `git checkout feature1`                 | Switches to branch `feature1`            |
| `git checkout -b <name>` | Create and switch branch        | `git checkout -b feature1`              | Creates and switches to `feature1`       |
| `git merge <name>`    | Merge branch into current         | `git merge feature1`                    | Combines `feature1` branch into current  |
| `git branch -d <name>`| Delete a branch                  | `git branch -d feature1`                | Deletes branch `feature1`                 |
| `git stash`           | Save uncommitted changes temporarily | `git stash`                          | Temporarily save your work to clean working dir |
| `git stash pop`       | Restore saved changes             | `git stash pop`                         | Reapply stashed changes                   |
| `git rm <file>`       | Remove a file                    | `git rm oldfile.txt`                    | Remove and stage the deletion             |
| `git mv <old> <new>`  | Rename or move a file             | `git mv file1.txt file2.txt`            | Rename file and stage change              |
</h6>



---

## Examples with Explanations

### Example 1: Initialize and Commit

```bash
mkdir myproject
cd myproject
git init                # Create Git repo
echo "Hello World" > README.md
git add README.md       # Stage file
git commit -m "Add README"  # Commit staged changes

```



<br>
<br>
<br>
<br>
<br>
<br>


## Git Shortcuts

##### Here’s a neat list of common Git keywords/shortcuts and what they stand for:

<h6> 

 | Shortcut/Keyword | Meaning / Full Command       | Explanation                                      |
|-----------------|-----------------------------|------------------------------------------------|
| rv              | remove (`git rm`)            | Remove file(s) from working dir & stage deletion |
| mv              | move/rename (`git mv`)       | Rename or move files and stage                   |
| .               | all in current directory (`git add .`) | Add all new & modified files in current directory |
| -A              | all (`git add -A`)           | Add all changes including deletions anywhere in repo |
| init            | initialize (`git init`)      | Create a new empty Git repository                |
| add             | add (`git add`)              | Add file(s) to staging area                       |
| commit          | commit (`git commit`)        | Save staged changes with a message                |
| status          | status (`git status`)        | Show current repo status                          |
| checkout        | checkout (`git checkout`)    | Switch branches or restore files                  |
| branch          | branch (`git branch`)        | Manage branches                                  |
| merge           | merge (`git merge`)          | Merge branches                                   |
| push            | push (`git push`)            | Upload commits to remote                          |
| pull            | pull (`git pull`)            | Download and merge from remote                    |
| clone           | clone (`git clone`)          | Copy a remote repo locally                        |
| log             | log (`git log`)              | View commit history                              |
| reset           | reset (`git reset`)          | Unstage files or reset commits                    |
| stash           | stash (`git stash`)          | Temporarily save changes                          |
| tag             | tag (`git tag`)              | Mark specific commits                            |
| fetch           | fetch (`git fetch`)          | Download objects and refs from remote without merging |
| rebase          | rebase (`git rebase`)        | Reapply commits on a new base                     |


</h6>

