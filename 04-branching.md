# Branching, Merging & Merge Conflicts

Git branches allow developers to work on features, bug fixes, and experiments independently without affecting the main codebase. Once the work is complete, branches can be merged back into the primary branch.

---

# Understanding Branches

A branch is an independent line of development within a Git repository.

Instead of making changes directly on the main branch, developers typically create feature branches where they can safely develop and test new functionality.

---

## Why Use Branches?

Branches help to:

- Keep the main branch stable.
- Develop features independently.
- Work on multiple tasks simultaneously.
- Reduce the risk of breaking production code.
- Enable collaboration among team members.

---

## Branch Structure

```text
main:
A --- B --- C --- D
```

Creating a feature branch:

```text
main:
A --- B --- C --- D
               \
                E --- F
```

After merging:

```text
A --- B --- C --- D --- G
               \       /
                E --- F
```

---

## Creating a Branch

```bash
# Create a new branch
git branch feature-login

# Switch to that branch
git checkout feature-login

# Or do both in one command
git checkout -b feature-login
```

Output:

```text
Switched to a new branch 'feature-login'
```

---

## View Available Branches

```bash
git branch
```

Example:

```text
  main
* feature-login
```

> The `*` symbol indicates the currently active branch.

---

## Switching Between Branches

```bash
# Switch to main branch
git checkout main

# Switch to feature branch
git checkout feature-login
```

---

## Example Workflow

```bash
# Start from the main branch
git checkout main

# Create and switch to a new branch
git checkout -b feature-login

# Create login.txt file
# Content: "Login Page Code"

# Stage and commit on feature branch
git add login.txt
git commit -m "Add login page"

# Make more changes
# Edit login.txt, add more code

git add login.txt
git commit -m "Complete login functionality"
```

View commit history:

```bash
git log --oneline
```

Example:

```text
f3e2d1c Complete login functionality
a9b8c7d Add login page
5h4i3j2 Previous main commit
```

---

## Deleting Branches

```bash
# Delete a branch (after merging)
git branch -d feature-login

# Force delete (even if not merged)
git branch -D feature-login
```

---

# Merging Branches

Merging combines changes from one branch into another.

Typically, feature branches are merged back into the main branch after development is complete.

---

## Repository Setup

```bash
mkdir git-merge-demo
cd git-merge-demo
git init

# Create the first file and make the initial commit
echo "Initial Code" > app.txt
git add .
git commit -m "initial commit"
```

---

# Fast-Forward Merge

A fast-forward merge occurs when the target branch has not changed since the feature branch was created.

Before:

```text
main:     A
           \
feature:    B --- C
```

After:

```text
main:     A --- B --- C
```

### Example

```bash
# Step 1: Create and switch to feature branch
git switch -c feature

# Step 2: Create a new file and commit
echo "Feature Code" > feature.txt
git add .
git commit -m "added feature file"

# Step 3: Switch back to main
git switch main

# Step 4: Merge
git merge feature
```

---

# Three-Way Merge

A three-way merge occurs when both branches contain new commits.

Before:

```text
main:          A --- B --- C
                        \
feature:                  D
```

After:

```text
main:          A --- B --- C --- M
                        \       /
feature:                  D ---
```

### Example

```bash
# Step 1: Create login-feature branch
git switch -c login-feature

# Step 2: Add a file on the feature branch
echo "Login Feature" > login.txt
git add .
git commit -m "added login"

# Step 3: Switch back to main and add a different file
git switch main
echo "Main Update" > main.txt
git add .
git commit -m "main updated"

# Step 4: Merge with -m to avoid Vim editor
git merge login-feature -m "three way merge completed"
```

---

# Squash Merge

A squash merge combines all feature branch commits into a single commit.

### Example

```bash
# Step 1: Create ui-feature branch
git switch -c ui-feature

# Step 2: Make multiple commits
echo "Navbar" > navbar.txt
git add .
git commit -m "navbar added"

echo "Footer" > footer.txt
git add .
git commit -m "footer added"

echo "Sidebar" > sidebar.txt
git add .
git commit -m "sidebar added"

# Step 3: Switch to main
git switch main

# Step 4: Squash merge (stages all changes but does NOT commit yet)
git merge --squash ui-feature

# Step 5: Commit manually with one clean message
git commit -m "UI Feature Complete"
```

---

# Octopus Merge

Octopus merge allows multiple branches to be merged simultaneously.

### Example

```bash
# Branch 1: feature-a
git switch -c feature-a
echo "A Feature" > a.txt
git add .
git commit -m "feature a"

# Branch 2: feature-b
git switch main
git switch -c feature-b
echo "B Feature" > b.txt
git add .
git commit -m "feature b"

# Branch 3: feature-c
git switch main
git switch -c feature-c
echo "C Feature" > c.txt
git add .
git commit -m "feature c"

# Switch to main and merge all three at once
git switch main
git merge feature-a feature-b feature-c -m "octopus merge all features"
```

---

# Merge Conflicts

A merge conflict occurs when Git cannot automatically combine changes from different branches.

This typically happens when the same section of a file has been modified in multiple branches.

---

## Creating a Conflict

```bash
# Main branch
git checkout main

# Edit score.txt, line 1: "Total Score: 100"
git add score.txt
git commit -m "Set score to 100"

# Feature branch
git checkout -b feature-scoring

# Edit score.txt, line 1: "Total Score: 200"
git add score.txt
git commit -m "Set score to 200"

# Try to merge
git checkout main
git merge feature-scoring
```

Output:

```text
Auto-merging score.txt
CONFLICT (content): Merge conflict in score.txt
Automatic merge failed; fix conflicts and then commit the result.
```

---

## Conflict Markers

Git inserts markers inside the file:

```text
<<<<<<< HEAD
Total Score: 100
=======
Total Score: 200
>>>>>>> feature-scoring
```

### Meaning

| Marker                    | Description             |
| ------------------------- | ----------------------- |
| `<<<<<<< HEAD`            | Current branch version  |
| `=======`                 | Separator               |
| `>>>>>>> feature-scoring` | Incoming branch version |

---

## Resolving a Conflict

Open the file and choose the final content.

Example:

```text
Total Score: 200
```

Remove all conflict markers and save the file.

Stage the resolved file:

```bash
git add score.txt
```

Complete the merge:

```bash
git commit -m "Resolve merge conflict - use score 200"
```

---

## Check Conflicted Files

```bash
git status
```

Example:

```text
Unmerged paths:
  both modified: score.txt
```

---

## Cancel a Merge

If you want to stop the merge process:

```bash
git merge --abort
```

---

# Conflict Resolution Workflow

```text
Create Branch
      ↓
Make Changes
      ↓
Merge Branches
      ↓
Conflict Detected
      ↓
Open File
      ↓
Resolve Conflict
      ↓
git add
      ↓
git commit
```

---

# Merge Comparison Table

| Merge Type   | Merge Commit Created?  | Command                      |
| ------------ | ---------------------- | ---------------------------- |
| Fast Forward | No                     | `git merge feature`          |
| Three-Way    | Yes                    | `git merge feature -m "msg"` |
| Squash       | One Clean Commit       | `git merge --squash feature` |
| Octopus      | Yes (Multiple Parents) | `git merge a b c -m "msg"`   |

---

# Summary

Git branches allow isolated development, merging combines completed work, and merge conflicts occur when Git cannot automatically determine which changes should be kept.

Basic workflow:

```text
Create Branch
      ↓
Make Changes
      ↓
Commit Changes
      ↓
Merge Branch
      ↓
Resolve Conflicts (if any)
      ↓
Continue Development
```
