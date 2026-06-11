# Remote Branches

When using GitHub, branches can exist in two locations:

- **Local Branches** — Stored on your computer.
- **Remote Branches** — Stored in the remote repository (GitHub).

Remote branches allow developers to share their work, collaborate on features, and synchronize changes across different machines.

---

# Local vs Remote Branches

```text
Local Repository                GitHub Repository
----------------                ----------------
main                            origin/main
feature-login                   origin/feature-login
```

A local branch is used for development, while a remote branch acts as the shared version available on GitHub.

---

# Publishing a Branch to GitHub

After creating and committing changes on a local branch, the branch can be uploaded to GitHub.

```bash
# Create a feature branch locally
git checkout -b feature-login

# Make changes and commit
git add login.txt
git commit -m "Add login page"

# Push branch to GitHub
git push -u origin feature-login
```

Example output:

```text
To https://github.com/example/project.git
 * [new branch]      feature-login -> feature-login
```

### What Happens?

- A new branch is created on GitHub.
- The local branch is linked to the remote branch.
- Future pushes and pulls can be performed without specifying the branch name repeatedly.

---

# Viewing Branches

### Display Local Branches

```bash
git branch
```

Example:

```text
* main
  feature-login
```

---

### Display Local and Remote Branches

```bash
git branch -a
```

Example:

```text
* main
  feature-login
  remotes/origin/main
  remotes/origin/feature-login
```

### Understanding the Output

| Branch                         | Description                     |
| ------------------------------ | ------------------------------- |
| `main`                         | Local main branch               |
| `feature-login`                | Local feature branch            |
| `remotes/origin/main`          | Remote main branch on GitHub    |
| `remotes/origin/feature-login` | Remote feature branch on GitHub |

---

# Accessing a Remote Branch

Before working with a branch that exists on GitHub, download the latest branch information.

```bash
git fetch origin
```

Then switch to the branch:

```bash
git checkout feature-login
```

Example output:

```text
Branch 'feature-login' set up to track remote branch 'feature-login' from 'origin'.
```

This creates a local branch connected to the corresponding branch on GitHub.

---

# Removing a Remote Branch

Once a feature is completed and no longer needed, the remote branch can be deleted from GitHub.

```bash
# Delete branch from GitHub
git push origin --delete feature-login
```

---

# Removing a Local Branch

Delete the local copy of the branch:

```bash
# Delete local branch
git branch -d feature-login
```

---

# Typical Remote Branch Workflow

```text
Create Branch
      ↓
Make Changes
      ↓
Commit Changes
      ↓
Push Branch to GitHub
      ↓
Collaborate / Review
      ↓
Merge Branch
      ↓
Delete Branch
```

---

# Summary

Remote branches make collaboration possible by storing branches on GitHub.

Common operations include:

```bash
git push -u origin feature-login
git branch
git branch -a
git fetch origin
git checkout feature-login
git push origin --delete feature-login
git branch -d feature-login
```

These commands allow developers to create, share, access, and remove branches across local and remote repositories.
