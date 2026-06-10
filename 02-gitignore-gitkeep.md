# `.gitignore` and `.gitkeep`

Managing files is an important part of working with Git. Not every file in a project should be stored in version control, and sometimes Git needs a little help tracking empty directories.

---

# Understanding `.gitignore`

The `.gitignore` file allows you to specify files and folders that Git should skip when checking for changes.

Without a `.gitignore` file, Git attempts to track every file inside your project directory.

---

## When Should Files Be Ignored?

Consider a web application project that contains:

- Secret credentials
- Generated log files
- Temporary project data
- Dependency folders

These files are often unnecessary or unsafe to store in a repository.

The `.gitignore` file prevents Git from tracking them.

---

## Creating a `.gitignore` File

Create a file named `.gitignore` in the root directory of your project.

Add the files and directories that should be excluded from version control.

```gitignore
# Ignore password file
passwords.txt

# Ignore entire temp folder
temp/

# Ignore all log files
*.log

# Ignore config folder
config/
```

---

## Example Workflow

Imagine a project contains sensitive credentials, temporary files, and installed dependencies.

Create a `.gitignore` file and add the following entries:

```bash
# Create .gitignore file
# (Use text editor to create file named: .gitignore)

# Add these lines:

passwords.txt
temp/
*.log
node_modules/

# Now stage and commit the .gitignore file itself
git add .gitignore
git commit -m "Add gitignore file"

# Git will now ignore those files
git status
```

Output:

```text
nothing to commit, working tree clean
```

Files matching the listed patterns will no longer appear in Git status checks.

---

## Common Ignore Rules

| Pattern          | Description                                    |
| ---------------- | ---------------------------------------------- |
| `filename.txt`   | Ignore a single file                           |
| `folder/`        | Ignore an entire directory                     |
| `*.log`          | Ignore all log files                           |
| `temp*`          | Ignore files beginning with "temp"             |
| `!important.log` | Include a file that would otherwise be ignored |

---

# Understanding `.gitkeep`

Git tracks files, not folders.

If a directory contains no files, Git treats it as non-existent and does not include it in the repository.

This can become a problem when you want a folder structure to exist before files are added.

---

## Why Use `.gitkeep`?

Suppose your application stores user uploads inside an `uploads` directory.

At the start of development, the folder is empty, but you still want everyone who clones the project to receive that directory.

Since Git cannot track an empty folder, a placeholder file is added.

The common convention is to name this placeholder `.gitkeep`.

---

## Example

```bash
# Create uploads folder
mkdir uploads

# Create .gitkeep file inside it
# (Use text editor to create empty file: uploads/.gitkeep)

# Now Git can track the folder
git add uploads/.gitkeep
git commit -m "Add uploads directory"
```

Once committed, the folder becomes part of the repository because it contains a tracked file.

---

## Important Note

`.gitkeep` is not an official Git command or built-in feature.

It is simply a widely accepted naming convention used by developers to keep otherwise empty directories under version control.

The file itself can be empty, and its only purpose is to ensure the directory exists in the repository.
