# Basic Git Commands

These are the fundamental Git commands that you'll use regularly while managing and tracking your projects.

---

## git init - Create a Git Repository

This command initializes Git in an existing folder, allowing Git to start tracking changes within that project.

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

## git status - View Repository Status

This is the command you will use most often. It shows:

- Modified files
- Staged files
- Untracked files
- Current branch information

```bash
git status
```

---

## git add - Prepare Changes for Commit

Move files from the **Working Directory** to the **Staging Area**.

### Stage a Specific File

```bash
git add <file_name>
```

### Stage Multiple Files

```bash
git add main.py app.py
```

### Stage All Changed Files

```bash
git add .
```

---

## git commit - Record Changes Permanently

A commit creates a snapshot of all staged changes, allowing you to save your work and maintain a history of updates.

```bash
git commit -m "messages that is relevant to the changes or commited file"
```

### Examples of clear Commit Messages

```bash
git commit -m "Add login page"
git commit -m "Fix bug"
git commit -m "Update design"
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

# Example: First Day at school

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
