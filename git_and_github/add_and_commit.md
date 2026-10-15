# Add and Commit in Git

## 1. Introduction

Git is a version control system that tracks changes to files in a project.

Two important Git commands are:

- `git add` — stages changes for the next commit.
- `git commit` — saves the staged changes as a snapshot in the local repository.

**Important:** Committing saves changes locally. To upload commits to GitHub, you generally use `git push`.

## 2. Check Your Current Directory

Before working with a repository, check where you are in the terminal.

```bash
pwd
```

`pwd` stands for **Print Working Directory**. It displays your current location.

List all files and directories, including hidden ones:

```bash
ls -la
```

A repository might contain:

```text
my-first-repo/
├── .git/
└── README.md
```

- `README.md` contains project documentation.
- `.git/` stores Git's repository data and history.

## 3. Check the Repository Status

Before making changes, check the current state of your repository.

```bash
git status
```

This command displays information such as:
- Your current branch.
- Whether your branch is ahead of or behind its remote counterpart.
- Modified, staged, and untracked files.
- Whether your working tree is clean.

### What does "working tree clean" mean?

It means Git has no detected uncommitted changes in the working tree or staging area.

If your local branch is also up to date with its remote counterpart, Git reports that status separately.

## 4. Create a New File

Create a text file named `test.txt`:

```bash
touch test.txt
```

Check the status again:

```bash
git status
```

Git will identify `test.txt` as an **untracked file**.

### What is an untracked file?

An untracked file is a file Git has not yet been instructed to track.

The file exists in your directory, but Git has not yet included it in the repository's tracked file history.

## 5. Stage a File Using `git add`

To stage the new file, run:

```bash
git add test.txt
```

Check the status:

```bash
git status
```

Git should now show `test.txt` under **Changes to be committed**.

### What is the staging area?

The staging area is where you prepare the changes you want included in your next commit.

Staging allows you to choose which changes to commit instead of committing every change in your working directory at once.

**Remember:** `git add` stages the file's current contents. If you edit the file again after staging it, you must stage the newer changes if you want them included in the next commit.

## 6. Unstage a File

If you accidentally stage a file, you can remove it from the staging area without deleting the file.

```bash
git restore --staged test.txt
```

Check the result:

```bash
git status
```

If `test.txt` was a new file and had never been committed, it will normally appear as untracked again.

For an already tracked file, its changes will return to the unstaged modified state.

**Important:** `git restore --staged` unstages changes; it does not discard the changes from your working file.

## 7. Commit Your Changes

Once you have staged the changes you want to save, create a commit:

```bash
git commit -m "Add test file"
```

### Understanding the command

- `git` invokes Git.
- `commit` saves the staged snapshot in the local repository.
- `-m` allows you to specify a commit message.
- `"Add test file"` describes the change.

### What is a commit?

A **commit** is a snapshot of the staged project changes, recorded in the local repository with metadata such as the author, date, and commit message.

Good commit messages briefly describe what changed.

Examples:

```bash
git commit -m "Add Git workflow notes"
git commit -m "Fix file handling exercise"
git commit -m "Update project README"
```

## 8. Verify Your Commit

After committing, run:

```bash
git status
```

If there are no remaining uncommitted changes, Git will report that the working tree is clean.

Your commit is now saved locally.

Git may also tell you that your branch is ahead of `origin/main` and suggest pushing your commits.

## 9. Push Your Commit to GitHub

To publish your local commit to the remote repository, run:

```bash
git push
```

This uploads your local commits to the configured remote branch, assuming the remote is configured and the push succeeds.

Without pushing, the commit remains in your local repository and is not automatically available on GitHub.

## 10. The Complete Add-and-Commit Workflow

```text
Create or edit a file
        |
        v
   git status
        |
        v
git add filename
        |
        v
   git status
        |
        v
git commit -m "Describe change"
        |
        v
   git status
        |
        v
     git push
        |
        v
Changes published to GitHub
```

### Commands to remember

| Command | Purpose |
|---|---|
| `pwd` | Display the current directory. |
| `ls -la` | List files, including hidden entries. |
| `git status` | Inspect the repository's current state. |
| `touch test.txt` | Create an empty file in a Unix-like shell. |
| `git add test.txt` | Stage the file. |
| `git restore --staged test.txt` | Unstage the file. |
| `git commit -m "Add test file"` | Save staged changes locally. |
| `git push` | Upload local commits to the remote repository. |

## 11. Key Takeaways

- **Untracked:** Git has not yet been instructed to track the file.
- **Staged:** Changes are selected for the next commit.
- **Committed:** Staged changes have been saved in the local repository.
- **Pushed:** Local commits have been uploaded to the remote repository.
- `git status` helps you check your progress at every stage.
- `git restore --staged` removes changes from staging without deleting the working file.
- `git add` and `git commit` are separate steps.
- A clean working tree does not necessarily mean your local branch is synchronized with GitHub.

## 12. Knowledge Check

1. What is the difference between an untracked file and a staged file?
2. What does `git add` do?
3. What does the `-m` flag mean in `git commit -m "message"`?
4. Does committing automatically upload your changes to GitHub?
5. Which command unstages a file without deleting it?
6. What does it mean when Git says your working tree is clean?
