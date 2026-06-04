## git commands 
# Hello my git repo commands useful list
`git add *` **all new files to satage**

`git add .` **all new files to satage**

`git add -A` **all new files to satage**

`git add [filename.txt]` **add the file only you want to commit**

`git remote prune [remote_name]` **in local cleaning/deleting remote_name remote!!**

`git log --oneline ` **to see the shorter log info**

`git log --oneline --graph [hash_code] ` **to see the with branch graph log info**

`git branch --no-merge ` **show the branchs list that no merges**

`git branch merge ` **show the branchs list that no merges**


I cleaned up your tutorial notes into a structured Markdown study guide while **keeping the original video/tutorial numbers like `[14]`, `[23]`, `[54 $$]`** so you can easily find the corresponding lesson later. The notes also explain **what the command does, when to use it, and common use cases**.

Source: Your uploaded Git tutorial notes. 

# Git Complete Study Notes

---

# [5] Clone a Repository

### Purpose

Download an existing Git repository from GitHub to your local machine.

### Command

```bash
git clone https://github.com/user/repo.git
```

### When to Use

* Joining an existing project.
* Downloading your own GitHub repository to another computer.

### Example

```bash
git clone https://github.com/sulusgit/hellogit.git
```

---

# [11] Git Configuration (Global vs Local)

### View Current Configuration

```bash
git config -l
```

### Global Configuration

Affects all repositories on your computer.

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

### Local Configuration

Only affects the current repository.

```bash
git config user.name "Project Name"
git config user.email "project@email.com"
```

### When to Use

* Global → personal projects.
* Local → company/work repositories using different credentials.

---

# [12] Remote Repositories

### What is a Remote?

A remote repository is an online Git repository (GitHub, GitLab, Bitbucket).

### Add Remote

```bash
git remote add origin https://github.com/user/repo.git
```

### View Remotes

```bash
git remote -v
```

### More Help

```bash
git remote --help
```

---

# [13] Most Common Git Commands

```bash
git init
git add
git commit
git status
git push
git pull
git clone
git checkout
git branch
git merge
```

---

# [14] Git File Lifecycle

A file moves through these states:

```text
Untracked
    ↓ git add
Staged
    ↓ git commit
Committed
    ↓ git push
Remote Repository
```

### States

| State     | Meaning                     |
| --------- | --------------------------- |
| Untracked | Git doesn't know about file |
| Modified  | File changed                |
| Staged    | Ready for commit            |
| Committed | Saved in local Git history  |
| Remote    | Uploaded to GitHub          |

### Useful Commands

```bash
git status
git log
```

---

# [15] Undo Staging

If you accidentally staged a file:

### Method 1

```bash
git restore --staged file.txt
```

### Method 2

```bash
git reset file.txt
```

### Method 3

```bash
git rm --cached file.txt
```

### When to Use

Remove files from staging without deleting them.

---

# [16] Restore Working Directory

### Method 1

```bash
git restore file.txt
```

### Method 2

```bash
git checkout -- file.txt
```

### When to Use

Discard local changes and restore file from latest commit.

⚠️ Changes will be lost.

---

# [17] Git Desktop Status

### Meaning

```text
(main -> origin)
```

Repository is connected to GitHub.

### Only

```text
(main)
```

Repository exists only locally.

---

# [18] Commits and SHA1 Hash

Every commit has a unique SHA1 hash.

Example:

```text
61987a23c1547b...
```

### Why Important?

* Identify commits.
* Restore old versions.
* Compare history.

### View Commit Details

```bash
git cat-file
```

---

# [19] Checkout Previous Commit

### Move to Old Commit

```bash
git checkout <hash>
```

### Example

```bash
git checkout 3341e51
```

### Detached HEAD

```text
HEAD detached at 3341e51
```

Means you are viewing history, not a branch.

---

# [20] HEAD

HEAD points to your current commit.

### View Branch Reference

```bash
cat .git/refs/heads/main
```

### Hidden Git Files

```bash
ls -la
```

---

# [21] Branch Management

### View Branches

```bash
git branch
```

### Create Branch

```bash
git branch dev
```

### Switch Branch

```bash
git checkout dev
```

### Rename Branch

```bash
git branch -m oldName newName
```

### Delete Branch

```bash
git branch -d test
```

---

# [22] Force Delete Branch

Delete even if not merged.

```bash
git branch -D branchName
```

⚠️ Use carefully.

---

# [23] Merge Branches

### Purpose

Combine changes from one branch into another.

### Best Practice

* Work on feature branches.
* Merge into `main` only when complete.

---

# [24] Fast Forward Merge

### Example

```bash
git checkout main
git merge login
```

### When Used

No conflicting history exists.

---

# [25, 26] Three-Way Merge

Used when both branches have different commits.

### Steps

```bash
git checkout main
git merge dev
```

### Requirement

Commit all changes first.

---

# [28 $$] Merge Conflicts

### Why Happens

Same lines edited in different branches.

### Resolve

1. Open file.
2. Choose correct code.
3. Remove conflict markers.

```text
<<<<<<< HEAD
=======
>>>>>>> branch
```

4. Commit changes.

```bash
git add .
git commit
```

---

# [30] Commit Messages

### Recommendation

Use present tense.

Good:

```text
add login page
fix bug in navbar
update README
```

Bad:

```text
added login page
fixed navbar
```

---

# [31-32 $$] Markdown Basics

### Heading

```md
# H1
## H2
### H3
```

### Bold

```md
**bold**
```

### Code

```md
`git status`
```

### Used For

README.md files.

---

# [35 $$] Push vs Pull vs Fetch

## Push

Upload local commits.

```bash
git push
```

---

## Fetch

Download remote changes only.

```bash
git fetch
```

No merge occurs.

---

## Pull

```bash
git pull
```

Equivalent to:

```bash
git fetch
git merge
```

---

# [36] Origin

`origin` = default name of remote repository.

Example:

```text
origin → github repository
```

---

# [40 $$] Fetch Command

### Purpose

Download latest remote information without changing working files.

```bash
git fetch
```

### Benefits

Safer than pull.

---

# [43] Git Prune

Remove deleted remote references.

```bash
git remote prune origin
```

---

# [44] FETCH_HEAD

Stores information about latest fetch.

Useful internally during merge operations.

---

# [45-47] Pull

### Pull = Fetch + Merge

```bash
git pull
```

### Conflict Solution

1. Fix manually.
2. Commit.

---

# [48-52] Push

### Push Current Branch

```bash
git push
```

### First Push of New Branch

```bash
git push -u origin newbranch
```

### Push All Branches

```bash
git push --all
```

---

# [53 $$] VS Code as Git Editor

```bash
git config core.editor "code --await"
```

---

# [54 $$] Why Fetch is Safer

Recommended workflow:

```bash
git fetch
git merge
```

Instead of:

```bash
git pull
```

Because you can inspect changes before merging.

---

# [55] Delete Remote Branch

```bash
git push origin -d branchName
```

---

# [56] Undo Operations

### Restore File

```bash
git restore file.txt
```

### Unstage File

```bash
git restore --staged file.txt
```

### Restore Everything

```bash
git restore .
```

### Remove Untracked Files

```bash
git clean -fd
```

---

# [57-60] Git Reset

## Hard Reset

```bash
git reset --hard HEAD~1
```

Resets:

* Working Tree
* Staging Area
* Repository

---

## Mixed Reset

```bash
git reset --mixed HEAD~1
```

Resets:

* Staging Area

Keeps:

* Working Tree

---

## Soft Reset

```bash
git reset --soft HEAD~1
```

Resets:

* Repository only

Keeps:

* Working Tree
* Staging Area

---

# [58 $$] Reflog

View all HEAD movements.

```bash
git reflog
```

Useful when recovering lost commits.

---

# [61 $$] Amend Last Commit

### Edit Last Commit Message

```bash
git commit --amend
```

### Add More Files to Last Commit

```bash
git add .
git commit --amend
```

---

# [62-63] Forking

### What is Fork?

Copy someone else's repository to your GitHub account.

### Used In

* Open-source contributions.
* Learning projects.

---

# [63 $$] Sync Fork With Original Repo

### Add Upstream

```bash
git remote add base <repo-url>
```

### Fetch Updates

```bash
git fetch base
```

### Merge Updates

```bash
git merge base/main
```

---

# [65-68] Pull Requests

### Closed Source Workflow

```text
feature branch
    ↓
pull request
    ↓
review
    ↓
merge
```

### Open Source Workflow

```text
Fork
 ↓
Branch
 ↓
Commit
 ↓
Push
 ↓
Pull Request
```

---

# [67] Branch Protection

Protect important branches.

Example:

* main
* production

Rules:

* No force push.
* Require pull requests.
* Require review before merge.

---

# [72] Semantic Versioning

Format:

```text
MAJOR.MINOR.PATCH
```

Example:

```text
2.12.4
```

### MAJOR

Breaking changes.

```text
2.x.x → 3.x.x
```

### MINOR

New features.

```text
2.11.0 → 2.12.0
```

### PATCH

Bug fixes.

```text
2.12.3 → 2.12.4
```

### Pre-release

```text
1.0.0-alpha
1.0.0-beta
1.0.0-rc.1
```

---

# [73] Git Tags

Mark important versions.

### Create Annotated Tag

```bash
git tag -a v1.0
```

### Create Lightweight Tag

```bash
git tag v1.0
```

### List Tags

```bash
git tag
```

### Show Tag Details

```bash
git show v1.0
```

### Push Tag

```bash
git push origin v1.0
```

### Push All Tags

```bash
git push origin --tags
```

### Delete Local Tag

```bash
git tag -d v1.0
```

### Delete Remote Tag

```bash
git push --delete origin v1.0
```

---

# [74] Git History Cleanup

Avoid many tiny commits.

Good:

```text
Add authentication system
```

Bad:

```text
fix1
fix2
fix3
fix4
```

---

# [75] Squash Merge

Combine multiple commits into one.

```bash
git merge --squash feature
```

### Benefit

Cleaner history.

---

# [76-78] Rebase

### Purpose

Move branch onto latest main branch.

```bash
git rebase main
```

### Benefits

* Cleaner history.
* Easier debugging.

### Drawback

Can affect teammates if used incorrectly.

---

# [78 $$] Rebase Conflict Handling

### Abort

```bash
git rebase --abort
```

### Continue

```bash
git rebase --continue
```

### View Differences

```bash
git diff
```

---

# [79 $$] Cherry Pick

Copy a single commit from another branch.

```bash
git cherry-pick <hash>
```

### Use When

Need only one commit, not whole branch.

---

# [80] Squash Merge on GitHub

GitHub allows:

```text
Merge Commit
Squash Merge
Rebase Merge
```

Recommended for many small commits:

```text
Squash Merge
```

---

# [81] Interactive Rebase

```bash
git rebase -i main
```

Used to:

* Squash commits.
* Reorder commits.
* Edit commit messages.
* Remove unwanted commits.

---

# [82] .gitignore

### Purpose

Ignore files Git should never track.

Example:

```gitignore
node_modules/
.env
dist/
*.log
```

### When to Use

* Dependencies.
* Secrets.
* Build files.
* Temporary files.

---

# Quick Git Workflow (Daily Use)

```bash
git pull

git checkout -b feature/login

# code...

git add .
git commit -m "add login validation"

git push -u origin feature/login

# create Pull Request

git checkout main
git pull
```

This note covers the Git topics from **[5] → [82]** in a cleaner study-guide format while preserving your original tutorial numbering for quick reference. 
