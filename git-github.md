# Table of Contents

<h6>  

| Topic                     | Link                                               |
|---------------------------|----------------------------------------------------|
| Git Add Command Guide     | [Git Add Command Guide](#git-add-command-guide)    |
| GitHub Tech step by step  | [GitHub Tech step by step](#github-tech-step-by-step) |
| Git & GitHub Basic Commands | [Git & GitHub Basic Commands](#git--github-basic-commands) |
</h6>
 
`Untracked`  —	New file, Git doesn’t know about it yet
<br>
`Unstaged` —	File is modified, but not added to staging area(only changed in your working directory)
<br>
`Staged` —	File is marked to be committed (you've already done git add)
<br>
`Committed` —	File is saved in repository history
<br>
`HEAD` —	The latest commit on the current branch




### 🔄 Transition Summary 

|     Action      |       From → To         |          Command             |
|-----------------|--------------------------|------------------------------|
| Modify a file   | Untracked → Modified *(Unstaged)*     |edit the file |
| Stage a file    | Modified → Staged        | `git add file.txt`           |
| Commit a file   | Staged → Committed       | `git commit -m "message"`    |

 
<br> 


## 1 📜 View Commit History

```bash
git log                        # Show commit hash, author, date, messages
git log --oneline              # Show commit in shortened format
git log -n 5                   # Show the last 5 commits

git log origin/main..HEAD      # Show commits on your branch that haven’t been pushed yet
git log --oneline --graph --all  # Visualize branch/merge history in a graph view

git show                       # Show details of the latest commit
git show HEAD                  # Show your latest commit details
git show --stat                # Show summary of changed files in the commit

gitk                           # GUI-style commit viewer (requires installation)
```

## 2 🔧 Reset Customization

#### 🔹 1. 🔄 Restore Working Directory (Unstaged)
###### 👉 This reverts the file(s) to the last committed version. Useful to undo changes **before staging**.
```bash
git restore filename.txt   # Restore a specific file
git restore .              # Restore all files
```

#### 🔹 2. 🔄 Unstage Staged File
###### You staged it (git add), but want to undo that: | This removes it from staging area, but Not changes in your file.
```bash
git restore --staged filename.txt
```



#### 🔹 3. 🔄 Discard All Changes (Staged + Working)
###### Restore everything to the last commit: will undo state and will change undo file
```bash 
git restore --source=HEAD --staged --worktree .
Or use:
git reset --hard  #⚠️ This will discard all unstaged AND staged changes.
```


#### 🔹 4. 🕒 Undo Last Commit (Keep Changes)

```bash
git reset --soft HEAD~1   # Undo commit, not undo staged and files
git reset --mixed HEAD~1  # Undo commit, Undo staged, but not change files
git reset --hard HEAD~1   # Undo commit, Undo staged, undo all files (⚠️ irreversible)
```

#### 🔹 5. 🔙 Reset to a Specific Commit 

```
git reset --hard <commit_hash>
```


## 3. BRANCHING
Command	Description 

```bash
git branch                   # List all local branches
git branch new-feature       # Create a new branch
git checkout new-feature     # Switch to an existing branch
git checkout -b new-feature  # Create and switch to a new branch
git merge branch-name        # Merge a branch into the current branch
git branch -d branch-name    # Delete a branch (only if merged)
git branch -D feature-x      # Force delete a branch without merging

```

## 4. 👀 Inspect & Compare

Used to analyze differences between commits, branches, or files.

```bash
git diff                # See changes in working directory (unstaged)
git diff --staged       # See changes that are staged for commit
git diff main..dev      # Compare changes between two branches
git diff --cached       # Compare staged changes vs last commit

git blame file.txt      # Show who last modified each line of a file

git log                 # View commit history
git log --graph         # Visual commit history tree
```

## 5. 📂 .gitignore & Git Clean

##### 🔧 Create `.gitignore` file:
```bash
touch .gitignore              # Create a .gitignore file to tell Git which files/folders to ignore
git status --ignored          # View ignored files
```



### 🧹 git clean

Used to remove **untracked files or directories** from your working directory.  
⚠️ **Warning:** This can permanently delete files!

```bash
git clean -n    # Dry run – show what would be deleted
git clean -f    # Force delete untracked files
git clean -fd   # Force delete untracked files and directories
```


## 6. 🧳 Git Stash
Temporarily save uncommitted changes and return to a clean state.
```bash
git stash                  # Save your current uncommitted changes
git stash pop              # Apply the most recent stash and remove it from stash list
git stash list             # View all saved stashes
git stash apply stash@{1}  # Apply a specific stash (without removing it)
git stash drop stash@{0}   # Delete a specific stash
git stash clear            # Remove all stashes
```

## 7. 🌐 Remote Repositories
Remote repos (like GitHub, GitLab) are online versions of your local repo.
```bash
git remote add origin https://github.com/your-name/your-repo.git  # Add remote origin
git remote -v                 # View configured remotes
git push origin main          # Push local changes to the main branch
git pull origin main          # Pull latest changes from the main branch
git clone https://github.com/user/repo.git  # Clone a remote repository
```



## 8. 🎯 Git Tags
Tags are used to mark specific points (commits) in history — commonly used for versioning and releases.
```bash
git tag v1.0.0                          # Create a lightweight tag
git tag -a v1.0.0 -m "Initial release" # Create an annotated tag with a message
git tag                                # List all tags
git push origin v1.0.0                 # Push a specific tag to the remote
```



<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>













---

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
git branch                   # List all local branches
git branch new-feature       # Create a new branch
git checkout new-feature     # Switch to an existing branch
git checkout -b new-feature  # Create and switch to a new branch
git merge branch-name        # Merge a branch into the current branch
git branch -d branch-name    # Delete a branch (only if merged)
git branch -D feature-x      # Force delete a branch without merging

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

