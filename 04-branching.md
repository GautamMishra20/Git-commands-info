# Understanding Branches

Branches allow developers to work on different tasks independently without affecting the primary codebase. They are one of Git's most important features for managing development workflows.

---

# Why Branches Matter

In a software project, the main branch often contains the stable version of the application.

When developing a new feature, fixing bugs, or experimenting with changes, working directly on the main branch can introduce problems into the stable code.

Branches provide an isolated workspace where changes can be developed and tested safely before being integrated into the main project.

---

# How Branches Work

Consider a repository with several commits on the main branch.

```text
main:
A --- B --- C --- D
```

A new feature branch is created from the latest commit.

```text
main:
A --- B --- C --- D
               \
                E --- F
```

Development continues on the feature branch without affecting the main branch.

Once the work is completed and tested, the branch can be merged back.

```text
A --- B --- C --- D --- G
               \         /
                E ----- F
```

This allows the main branch to remain stable throughout development.

---

# Creating a Branch

Create a new branch:

```bash
# Create a new branch
git branch feature-login
```

Switch to the branch:

```bash
# Switch to that branch
git checkout feature-login
```

Create and switch in a single command:

```bash
# Or do both in one command
git checkout -b feature-login
```

Output:

```text
Switched to a new branch 'feature-login'
```

---

# Viewing Available Branches

Display all local branches:

```bash
git branch
```

Example output:

```text
  main
* feature-login
```

> The `*` symbol identifies the branch currently in use.

---

# Switching Between Branches

Move to the main branch:

```bash
# Switch to main branch
git checkout main
```

Move back to the feature branch:

```bash
# Switch to feature branch
git checkout feature-login
```

Git automatically updates the working directory to match the selected branch.

---

# Example Workflow

The following example demonstrates a typical feature development process.

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

View the commit history for the branch:

```bash
git log --oneline
```

Example output:

```text
f3e2d1c Complete login functionality
a9b8c7d Add login page
5h4i3j2 (main) Previous main commit
```

Switch back to the main branch:

```bash
git checkout main
```

The files that exist only on the feature branch are no longer visible.

Return to the feature branch:

```bash
git checkout feature-login
```

The feature branch files become available again.

---

# Deleting Branches

After a branch has served its purpose, it can be removed.

Delete a merged branch:

```bash
# Delete a branch (after merging)
git branch -d feature-login
```

Force deletion:

```bash
# Force delete (even if not merged)
git branch -D feature-login
```

> Use force deletion carefully, as unmerged work may be lost.

---

# Typical Branch Structure

A project may contain several branches dedicated to different tasks.

```text
main
├── feature-login
├── feature-ui-design
├── feature-database
└── feature-api
```

Each branch focuses on a specific piece of work, making development more organized and reducing the risk of conflicts.

---

# Benefits of Using Branches

- Keep the main branch stable.
- Develop features independently.
- Test changes before integration.
- Allow multiple developers to work simultaneously.
- Organize work into separate tasks or features.

---

# Summary

Branches create isolated environments for development.

Common workflow:

```text
Create Branch
      ↓
Make Changes
      ↓
Commit Changes
      ↓
Switch Branches
      ↓
Merge When Ready
```

By using branches effectively, teams can develop new features, fix bugs, and experiment with ideas without affecting the stable version of the project.
