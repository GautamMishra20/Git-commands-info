# Pull Requests

A Pull Request (PR) is a GitHub feature that allows developers to propose changes from one branch and request that those changes be merged into another branch.

Before code becomes part of the main branch, it can be reviewed, discussed, and tested through a Pull Request.

---

# Purpose of Pull Requests

Pull Requests help teams maintain code quality and improve collaboration during development.

### Code Review

Team members can inspect changes before they are merged into the project.

---

### Team Discussion

Developers can ask questions, provide feedback, and suggest improvements directly within the Pull Request.

---

### Quality Assurance

Potential bugs, errors, and coding issues can be identified before changes reach the main branch.

---

### Change Tracking

Pull Requests provide a clear record of what was changed, who made the changes, and why the changes were introduced.

---

# Pull Request Workflow

A typical Pull Request follows this process:

```text
Create Branch
      ↓
Make Changes
      ↓
Commit Changes
      ↓
Push Branch
      ↓
Create Pull Request
      ↓
Review Changes
      ↓
Approve Changes
      ↓
Merge Pull Request
```

---

# Creating a Pull Request

First, create a branch and push it to GitHub.

```bash
# Create feature branch
git checkout -b feature-login

# Make changes
git add login.txt
git commit -m "Add login page"

# Push branch to GitHub
git push -u origin feature-login
```

After the branch is available on GitHub:

1. Open the repository on GitHub.
2. Navigate to the **Pull Requests** tab.
3. Click **New Pull Request**.
4. Select the source branch and target branch.
5. Add a title and description.
6. Click **Create Pull Request**.

---

# Components of a Pull Request

## Title

A short summary of the proposed change.

Example:

```text
Add login page functionality
```

---

## Description

Provides details about the implementation and purpose of the changes.

Example:

```text
- Added login page UI
- Added form validation
- Improved user authentication flow
```

---

## Files Changed

Displays all modifications included in the Pull Request.

Reviewers can:

- View additions and deletions
- Compare file versions
- Leave comments on specific lines

---

# Reviewing a Pull Request

Reviewers examine the proposed changes before merging.

Common review activities include:

- Reading the modified code
- Testing the functionality
- Identifying issues
- Suggesting improvements
- Asking for clarification

---

# Review Outcomes

### Approve

The changes are accepted and ready to be merged.

---

### Request Changes

The contributor must address the requested modifications before merging.

---

### Comment

Feedback is provided without formally approving or rejecting the Pull Request.

---

# Merging a Pull Request

After approval, the Pull Request can be merged into the target branch.

```text
main
  │
  ├── feature-login
  │
  ▼
Pull Request
  │
  ▼
Review
  │
  ▼
Merge
```

Once merged, the feature branch's changes become part of the main branch.

---

# Benefits of Pull Requests

- Improve code quality
- Encourage collaboration
- Reduce bugs
- Maintain project history
- Provide transparency in development
- Support team-based workflows

---

# Best Practices

- Keep Pull Requests focused on a single feature or fix.
- Use clear and descriptive titles.
- Add meaningful descriptions.
- Review changes before requesting approval.
- Respond to review feedback promptly.
- Avoid extremely large Pull Requests whenever possible.

---

# Summary

A Pull Request is a structured way to propose and review code changes before they are merged into a project.

Typical process:

```text
Create Branch
      ↓
Develop Feature
      ↓
Commit Changes
      ↓
Push to GitHub
      ↓
Open Pull Request
      ↓
Review & Discussion
      ↓
Approval
      ↓
Merge
```

Pull Requests are a central part of modern GitHub workflows because they combine collaboration, code review, and change management into a single process.

# Forking, Pull Requests & Remote Branches

Open-source projects often allow anyone to contribute improvements, bug fixes, and new features. GitHub provides a workflow that makes this possible through **Forks**, **Remote Branches**, and **Pull Requests**.

---

# What is Forking?

A fork is a personal copy of another repository that is created under your own GitHub account.

The fork contains the complete project history and allows you to experiment, modify code, and develop features without affecting the original repository.

---

## Fork Workflow

```text
Original Repository
        │
        ▼
      Fork
        │
        ▼
 Clone Locally
        │
        ▼
 Make Changes
        │
        ▼
 Push Changes
        │
        ▼
 Pull Request
        │
        ▼
 Original Repository
```

---

# Step 1: Fork the Repository

1. Open the repository on GitHub.
2. Click the **Fork** button.
3. GitHub creates a copy of the repository under your account.

Example:

```text
Original Repository
github.com/project-owner/sample-project

          │
          ▼

Your Fork
github.com/your-username/sample-project
```

---

# Step 2: Clone Your Fork

Clone the forked repository to your local machine.

```bash
# Clone your fork
git clone git@github.com:your-username/school-project.git
cd school-project

# Check remotes
git remote -v
```

Example output:

```text
origin  git@github.com:your-username/school-project.git (fetch)
origin  git@github.com:your-username/school-project.git (push)
```

At this stage, `origin` points to your fork.

---

# Step 3: Add the Original Repository

To receive future updates from the original project, add another remote.

```bash
git remote add upstream git@github.com:project-owner/school-project.git

git remote -v
```

Example output:

```text
origin    git@github.com:your-username/school-project.git (fetch)
origin    git@github.com:your-username/school-project.git (push)
upstream  git@github.com:project-owner/school-project.git (fetch)
upstream  git@github.com:project-owner/school-project.git (push)
```

---

## Understanding Origin and Upstream

| Remote     | Purpose                 |
| ---------- | ----------------------- |
| `origin`   | Your forked repository  |
| `upstream` | The original repository |

```text
upstream
    │
    ▼
Original Repository

origin
    │
    ▼
Your Fork
```

---

# Step 4: Create a Feature Branch

Never work directly on the main branch when contributing.

Create a separate branch:

```bash
# Always create a new branch for your changes
git checkout -b fix-homepage

# Make changes — edit homepage.txt in your text editor

# Stage and commit
git add homepage.txt
git commit -m "Fix homepage title"
```

---

# Step 5: Push Changes to Your Fork

Upload the branch to your fork.

```bash
# Push to YOUR fork (origin), not upstream
git push origin fix-homepage
```

Example output:

```text
To git@github.com:your-username/school-project.git
 * [new branch]      fix-homepage -> fix-homepage
```

The branch now exists on GitHub.

---

# Step 6: Create a Pull Request

After pushing the branch:

1. Open your fork on GitHub.
2. Click **Compare & Pull Request**.
3. Verify the target repository and branch.
4. Add a meaningful title.
5. Add a clear description.
6. Click **Create Pull Request**.

---

## Pull Request Flow

```text
Feature Branch
      │
      ▼
Push to Fork
      │
      ▼
Pull Request
      │
      ▼
Code Review
      │
      ▼
Merge
```

---

# Step 7: Repository Maintainer Reviews the Changes

During review, maintainers may:

- Read the modified code
- Test the implementation
- Leave comments
- Request improvements
- Approve the contribution

Once approved, the Pull Request is merged into the main branch.

---

# Step 8: Synchronize Your Fork

After the Pull Request is merged, the original repository has new commits.

Update your local repository:

```bash
# Switch to main branch
git checkout main

# Pull latest from original repo
git pull upstream main
```

Example output:

```text
From github.com:project-owner/school-project
 * branch            main -> FETCH_HEAD
Updating a1b2c3d..f3e2d1c
Fast-forward
 homepage.txt | 1 +
```

Push the updates to your fork:

```bash
# Push the updated main to your own fork
git push origin main
```

Now:

- Local repository is updated.
- Fork is updated.
- Original repository changes are synchronized.

---

# Working with Remote Branches

A remote branch is a branch that exists on a remote repository such as GitHub.

Before working with remote branches, fetch the latest branch information.

```bash
# Fetch all remote branches
git fetch origin
```

---

## View Remote Branches

```bash
# See all remote branches
git branch -r
```

Example:

```text
origin/main
origin/feature-database
origin/fix-homepage
```

---

## Create a Local Branch from a Remote Branch

```bash
# Create a local branch that tracks the remote one
git checkout -b feature-database origin/feature-database
```

Example output:

```text
Branch 'feature-database' set up to track remote branch
'feature-database' from 'origin'.
```

The remote branch can now be used locally like any other branch.

---

## View Branch History

```bash
git log --oneline
```

Example:

```text
c3d4e5f (origin/feature-database) Add database connection
a1b2c3d Initial commit
```

---

# Contributing to an Existing Remote Branch

Make modifications:

```bash
# Edit database.txt
git add database.txt
git commit -m "Fix database connection string"
```

Push the changes:

```bash
# Push back to the same remote branch
git push origin feature-database
```

The updated commits are now available on GitHub.

---

# Receiving Updates from a Remote Branch

To download the latest changes from a branch:

```bash
# Pull the latest on the branch
git checkout feature-database
git pull origin feature-database
```

This synchronizes the local branch with the remote branch.

---

# Complete Contribution Workflow

```text
Fork Repository
        ↓
Clone Fork
        ↓
Add Upstream Remote
        ↓
Create Branch
        ↓
Make Changes
        ↓
Commit Changes
        ↓
Push to Fork
        ↓
Create Pull Request
        ↓
Review & Merge
        ↓
Sync Fork with Upstream
```

---

# Summary

Forking enables developers to contribute to repositories they do not own.

Key concepts:

| Concept       | Purpose                       |
| ------------- | ----------------------------- |
| Fork          | Personal copy of a repository |
| Origin        | Your fork                     |
| Upstream      | Original repository           |
| Remote Branch | Branch stored on GitHub       |
| Pull Request  | Request to merge changes      |

Together, forks, remote branches, and pull requests form the standard workflow used in most open-source projects.
