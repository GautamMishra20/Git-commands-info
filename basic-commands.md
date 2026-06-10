# Basic Git Commands

These are the essential commands you will use every day when working with Git.

---

## git init - Start Tracking a Folder

This command turns a normal folder into a Git repository. Run it once inside the folder you want to track.

```bash
# Navigate to your project folder
cd school-project

# Initialize Git
git init
```

Output:

```text
Initialized empty Git repository in /school-project/.git/
```

> Git creates a hidden `.git` folder inside. This is Git's database—do not delete or edit it manually.

---

## git status - Check What Changed

This is the command you will use most often. It shows:

- Modified files
- Staged files
- Untracked files
- Current branch information

```bash
git status
```

---

## git add - Stage Your Changes

Move files from the **Working Directory** to the **Staging Area**.

### Stage a Specific File

```bash
git add filename.txt
```

### Stage Multiple Files

```bash
git add file1.txt file2.txt
```

### Stage All Changed Files

```bash
git add .
```

---

## git commit - Save a Snapshot

Save all staged files permanently with a message describing what changed.

```bash
git commit -m "Your message here"
```

### Good Commit Messages

```bash
git commit -m "Add login page"
git commit -m "Fix score calculation bug"
git commit -m "Update homepage design"
```

### Avoid

```bash
git commit -m "Changes"
git commit -m "Update"
git commit -m "Fixed stuff"
```

> Write commit messages in present tense.

---

## git log - View History

See a list of all commits (snapshots) you have made.

### Full Detailed History

```bash
git log
```

### Compact One-Line History

```bash
git log --oneline
```

Example:

```text
a1b2c3d Add login page
9e8f7g6 Fix score bug
5h4i3j2 Initial commit
```

> Press `Q` to quit the log view.

---

## git diff - See What Changed

Shows the actual lines that were added, modified, or removed.

```bash
git diff
```

### Compare Staged Changes

```bash
git diff --staged
```

---

# Complete Example: Gian's First Day

```bash
# Create project folder
mkdir school-project

# Move into folder
cd school-project

# Initialize Git
git init

# Create a file (readme.txt)
# Content: School Project Tracker Project

# Check status
git status
```

Output:

```text
Untracked files:
  readme.txt
```

```bash
# Stage the file
git add readme.txt

# Commit the file
git commit -m "Add readme file"

# View commit history
git log --oneline
```

Output:

```text
a1b2c3d Add readme file
```

---

# Git Workflow

```text
Working Directory
       │
       ▼
    git add
       │
       ▼
  Staging Area
       │
       ▼
  git commit
       │
       ▼
   Repository
```

---

# Quick Reference Table

| Command                   | What It Does                   |
| ------------------------- | ------------------------------ |
| `git init`                | Start Git tracking in a folder |
| `git status`              | Check which files changed      |
| `git add filename`        | Stage one specific file        |
| `git add .`               | Stage all changed files        |
| `git commit -m "message"` | Save a permanent snapshot      |
| `git log`                 | View commit history            |
| `git log --oneline`       | View compact history           |
| `git diff`                | See line-by-line changes       |
| `git diff --staged`       | View staged changes            |

---

## Summary

The most commonly used Git commands are:

```bash
git status
git add .
git commit -m "message"
git log --oneline
git diff
```

Master these commands first—they form the foundation of everyday Git usage.
