# Git Tutorial

Git is a **distributed version control system** used to track changes in files and manage source code.

GitHub is a platform used to **store, share, and collaborate on Git repositories**.

---

## 1. Check Git Version

```bash
git --version
```

---

## 2. Configure Git

Set username:

```bash
git config --global user.name "Your Name"
```

Set email:

```bash
git config --global user.email "your@email.com"
```

Check configuration:

```bash
git config --list
```

---

## 3. Create a Git Repository

Initialize Git in a project:

```bash
git init
```

This creates a hidden `.git` directory.

```text
Project Folder
│
├── file.py
├── README.md
└── .git/
```

---

## 4. Check Repository Status

```bash
git status
```

Shows:

* Modified files
* Untracked files
* Staged files
* Current branch

---

## 5. Add Files

Add one file:

```bash
git add file.py
```

Add multiple files:

```bash
git add file1.py file2.py
```

Add all files:

```bash
git add .
```

---

## 6. Commit Changes

Commit staged changes:

```bash
git commit -m "Added Python program"
```

A commit creates a **snapshot of the project at that point in time**.

---

## 7. View Commit History

```bash
git log
```

Short version:

```bash
git log --oneline
```

---

## 8. Git Workflow

The basic Git workflow is:

```text
Working Directory
        ↓
     git add
        ↓
Staging Area
        ↓
   git commit
        ↓
Local Repository
        ↓
    git push
        ↓
     GitHub
```

---

## 9. Connect Local Repository to GitHub

Add remote repository:

```bash
git remote add origin https://github.com/username/repository.git
```

Check remote:

```bash
git remote -v
```

---

## 10. Push Code to GitHub

First push:

```bash
git push -u origin main
```

After that:

```bash
git push
```

### `origin`

`origin` is the default name given to the remote repository.

### `main`

`main` is the branch being pushed.

---

## 11. Clone Repository

Download an existing GitHub repository:

```bash
git clone https://github.com/username/repository.git
```

Then enter the folder:

```bash
cd repository
```

---

## 12. Pull Changes

Download and integrate changes from the remote repository:

```bash
git pull
```

Specify remote and branch:

```bash
git pull origin main
```

---

## 13. Fetch Changes

Download changes from the remote repository without automatically merging them:

```bash
git fetch
```

Fetch from a specific remote:

```bash
git fetch origin
```

Difference:

```text
git fetch
    ↓
Downloads remote changes

git pull
    ↓
Downloads + integrates changes
```

---

## 14. Branches

Create a branch:

```bash
git branch feature
```

View branches:

```bash
git branch
```

Switch branch:

```bash
git switch feature
```

Create and switch:

```bash
git switch -c feature
```

---

## 15. Delete Branch

Delete a local branch:

```bash
git branch -d feature
```

Force delete:

```bash
git branch -D feature
```

---

## 16. Merge Branch

Switch to the branch that should receive the changes:

```bash
git switch main
```

Merge another branch:

```bash
git merge feature
```

---

## 17. Merge Conflict

A merge conflict occurs when Git cannot automatically decide which changes to keep.

Example:

```text
<<<<<<< HEAD
Your changes
=======
Other branch changes
>>>>>>> feature
```

Resolve the file manually.

Then:

```bash
git add .
```

Commit:

```bash
git commit -m "Resolve merge conflict"
```

---

## 18. `.gitignore`

`.gitignore` tells Git which files or folders should **not be tracked**.

Example:

```text
.venv/
__pycache__/
.env
*.pyc
.DS_Store
```

Create:

```bash
touch .gitignore
```

---

## 19. Untracked Files

Check:

```bash
git status
```

Add an untracked file:

```bash
git add filename
```

---

## 20. Unstage a File

Remove a file from the staging area:

```bash
git restore --staged filename
```

The file is **not deleted**.

---

## 21. Discard Changes

Discard changes in a file:

```bash
git restore filename
```

Be careful because the changes may be lost.

---

## 22. Amend Last Commit

Change the most recent commit:

```bash
git commit --amend
```

Change the commit message:

```bash
git commit --amend -m "Updated commit message"
```

---

## 23. Git Diff

View unstaged changes:

```bash
git diff
```

View staged changes:

```bash
git diff --staged
```

---

## 24. Git Reset

Unstage a commit/file:

```bash
git reset
```

Reset to a previous commit:

```bash
git reset --hard HEAD~1
```

### Important

`--hard` can remove local changes.

Use it carefully.

---

## 25. HEAD

`HEAD` points to the **current commit/position in the current branch**.

Example:

```text
HEAD
 ↓
A → B → C
        ↑
       main
```

`HEAD~1` means:

```text
One commit before HEAD
```

---

## 26. Git Revert

Creates a new commit that reverses an earlier commit.

```bash
git revert <commit-id>
```

Unlike `reset`, `revert` keeps the existing history.

---

## 27. Git Reset vs Revert

```text
reset
→ Moves branch history backward

revert
→ Creates a new commit that undoes changes
```

For shared repositories, `revert` is generally safer.

---

## 28. Remote Repository

View remote:

```bash
git remote -v
```

Add remote:

```bash
git remote add origin URL
```

Change remote URL:

```bash
git remote set-url origin URL
```

Remove remote:

```bash
git remote remove origin
```

---

## 29. Rename Branch

Rename current branch to `main`:

```bash
git branch -M main
```

---

## 30. Push New Branch

```bash
git push -u origin feature
```

After setting upstream:

```bash
git push
```

---

## 31. Pull with Rebase

```bash
git pull --rebase origin main
```

This downloads remote changes and places your local commits on top of them.

---

## 32. Rebase

Rebase moves your commits onto another base.

```bash
git switch feature

git rebase main
```

Basic idea:

```text
Before:

A → B → C
     \
      D → E


After rebase:

A → B → C → D' → E'
```

---

## 33. Interactive Rebase

Used to modify commit history.

```bash
git rebase -i HEAD~3
```

Common commands:

```text
pick
reword
edit
squash
fixup
drop
```

### Meaning

```text
pick    → Keep commit
reword  → Change commit message
edit    → Edit commit
squash  → Combine commits
fixup   → Combine without keeping message
drop    → Remove commit
```

---

## 34. Abort Rebase

If something goes wrong:

```bash
git rebase --abort
```

Continue after resolving conflicts:

```bash
git rebase --continue
```

---

## 35. Abort Merge

Cancel an ongoing merge:

```bash
git merge --abort
```

---

## 36. Stash

Temporarily save uncommitted changes.

```bash
git stash
```

View stashes:

```bash
git stash list
```

Restore latest stash:

```bash
git stash pop
```

Apply without removing stash:

```bash
git stash apply
```

---

## 37. Tags

Create a tag:

```bash
git tag v1.0
```

View tags:

```bash
git tag
```

Push tag:

```bash
git push origin v1.0
```

---

## 38. Show Commit

Show details of a commit:

```bash
git show <commit-id>
```

---

## 39. Find Commit

Search commits by message:

```bash
git log --grep="message"
```

---

## 40. Delete Remote Branch

```bash
git push origin --delete feature
```

---

## 41. Common Git Errors

### Remote origin already exists

```text
error: remote origin already exists
```

Check:

```bash
git remote -v
```

Change it:

```bash
git remote set-url origin URL
```

---

### Push Rejected

Example:

```text
rejected
fetch first
```

Usually means the remote has commits that your local repository does not have.

Try:

```bash
git pull origin main
```

Then:

```bash
git push origin main
```

---

### Merge Conflict

Check:

```bash
git status
```

Resolve the conflicting files.

Then:

```bash
git add .
git commit -m "Resolve merge conflict"
git push
```

---

### Wrong Remote Name

Correct:

```bash
git push origin main
```

Incorrect:

```bash
git push orign main
```

---

## 42. Useful Git Commands

| Command       | Use                      |
| ------------- | ------------------------ |
| `git init`    | Create repository        |
| `git status`  | Check status             |
| `git add .`   | Stage files              |
| `git commit`  | Save changes             |
| `git log`     | View history             |
| `git clone`   | Download repository      |
| `git push`    | Upload changes           |
| `git pull`    | Download + integrate     |
| `git fetch`   | Download remote changes  |
| `git branch`  | Manage branches          |
| `git switch`  | Switch branches          |
| `git merge`   | Merge branches           |
| `git rebase`  | Reapply commits          |
| `git stash`   | Temporarily save changes |
| `git restore` | Restore files            |
| `git reset`   | Move/reset history       |
| `git revert`  | Undo with new commit     |
| `git diff`    | View changes             |
| `git remote`  | Manage remote            |
| `git tag`     | Create tags              |

---

# CHEAT SHEET

```bash
git init

git status

git add .

git commit -m "Message"

git log --oneline

git remote add origin URL

git remote -v

git branch

git switch -c feature

git switch main

git merge feature

git pull origin main

git push -u origin main

git clone URL

git fetch

git stash

git stash pop

git diff

git restore filename

git restore --staged filename

git revert <commit-id>

git reset --hard HEAD~1

git rebase main

git rebase --abort

git merge --abort
```

