# Undoing Changes in Git

While working on a project, there may be times when you stage the wrong file, modify content by mistake, or create a commit that you don't want anymore. Git provides several ways to reverse these actions depending on where the change exists.

---

# Removing Files from the Staging Area

Sometimes a file is added to the staging area accidentally and should not be included in the next commit.

To move a staged file back to the working directory:

```bash id="x7lpsk"
# accidentally staged wrong file
git add <filename>

# Unstage it
git restore --staged <filename>
```

To remove all staged files at once:

```bash id="t7n7qn"
git restore --staged .
```

After running these commands, the files remain unchanged, but they are no longer prepared for commit.

---

# Discarding Uncommitted Changes

If you modify a file and later decide that those edits are unnecessary, Git can restore the file to its last committed state.

Restore a single file:

```bash id="yzg4ly"
git restore filename.txt
```

Restore all modified files:

```bash id="cw7n7n"
git restore .
```

> Any unsaved work removed using `git restore` cannot be recovered later.

---

# Undoing Recent Commits

Occasionally a commit may be created too early or contain incorrect changes. Git offers different reset options depending on what you want to keep.

---

## Soft Reset

Removes the commit but keeps all changes staged and ready for another commit.

```bash id="lf8xrn"
# Undo last commit, keep changes in staging area
git reset --soft HEAD~1
```

Use this when you only want to rewrite the commit or adjust its message.

---

## Mixed Reset

Removes the commit and unstages the changes, but keeps the modified files.

```bash id="66o7rw"
# Undo last commit, keep changes but unstage them
git reset HEAD~1
```

This is useful when you want to review or reorganize the changes before committing again.

---

## Hard Reset

Removes both the commit and all associated changes.

```bash id="2k5w8m"
# Undo last commit and DELETE all changes
git reset --hard HEAD~1
```

> This action permanently removes your work from the current branch.

---

# Returning to an Older Commit

You can move your repository back to a previous point in history using a commit hash.

First, view the available commits:

```bash id="sn44ul"
# View commit history
git log --oneline
```

Example:

```text id="pdvy04"
a1b2c3d Latest commit
9e8f7g6 Previous commit
5h4i3j2 Old commit
1k2l3m4 Very old commit
```

Reset to a specific commit:

```bash id="0m4p4l"
# Go back to specific commit
git reset 5h4i3j2
```

The repository will return to the selected point in history.

---

# Reverting Changes Safely

In many situations, especially after code has been shared with others, removing commit history is not recommended.

Instead, Git can create a new commit that reverses the effects of an earlier one.

```bash id="4yzquu"
# Safely undo a specific commit
git revert 9e8f7g6
```

Git then opens an editor for the commit message.

```text id="e0jwmr"
# Git opens editor for commit message
# Save and close - a new "revert" commit is created
```

This approach preserves project history while canceling unwanted changes.

---

# Example Scenario

Suppose a developer updates a file with incorrect information and stages it accidentally.

```bash id="u0h57z"
# Nobita edits score.txt
# He adds wrong data

# He stages it
git add score.txt

# Wait! He realizes the mistake
# Unstage the file
git restore --staged score.txt

# Discard the wrong changes
git restore score.txt
```

Result:

```text id="49hjlwm"
# File is back to last committed version
```

The file returns to the exact state stored in the most recent commit.

---

# Choosing the Right Command

| Situation                              | Recommended Command       |
| -------------------------------------- | ------------------------- |
| Remove a file from staging             | `git restore --staged`    |
| Discard local file changes             | `git restore`             |
| Undo a commit but keep changes staged  | `git reset --soft HEAD~1` |
| Undo a commit and unstage changes      | `git reset HEAD~1`        |
| Remove a commit and all changes        | `git reset --hard HEAD~1` |
| Undo a commit without deleting history | `git revert`              |

---

# Key Recommendations

- Prefer `git revert` when working with commits that have already been shared.
- Use `git reset` mainly for local commits that have not been pushed.
- Double-check before using `--hard` because the removed changes cannot be restored through Git.
- Review your changes carefully before undoing them to avoid accidental data loss.
