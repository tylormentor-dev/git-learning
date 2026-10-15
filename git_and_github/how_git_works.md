# How Git Works

## 1. What Is Git?

**Git** is a distributed version control system that tracks changes to files over time.

Git allows developers to:
- Track changes to files.
- Save snapshots of their work.
- Return to previous versions.
- Work on different features using branches.
- Collaborate with other developers.

## 2. What Is GitHub?

**GitHub** is a cloud-based hosting platform for Git repositories.

It allows developers to store repositories online, share code, collaborate on projects, and accept contributions from other developers.

### Git vs GitHub

| Git | GitHub |
|---|---|
| A version control system. | A platform that hosts Git repositories. |
| Runs locally on your computer. | Provides online repository hosting and collaboration tools. |
| Tracks file changes and commits. | Allows you to share and manage repositories online. |

## 3. Understanding the `.git` Directory

When you clone a repository, you download its files and Git repository data to your computer.

For example, a repository may contain:

```text
my-first-repo/
├── .git/
└── README.md
```

### What is `.git`?

The `.git` directory stores the internal information Git needs to manage the repository, including its history, configuration, and references.

**Important:** Do not delete `.git` if you want to preserve the directory as a functioning Git repository.

### Why is `.git` hidden?

On Unix-like systems, filenames beginning with a dot are generally hidden by default.

To display hidden files and directories, run:

```bash
ls -la
```

- `ls` lists directory contents.
- `-l` displays a detailed listing.
- `-a` includes hidden entries.

### What does `git init` do?

The command:

```bash
git init
```

Initializes a new Git repository in the current directory, creating the repository metadata Git needs.

When you create a repository directly on GitHub and then clone it, you normally do not need to run `git init` yourself.

## 4. The Git Workflow

Git's basic workflow involves three main areas:

1. Working directory
2. Staging area
3. Local repository (committed history)

Changes can then be shared with a remote repository, such as one hosted on GitHub.

### The workflow diagram

```text
Working Directory
       |
       | git add
       v
 Staging Area
       |
       | git commit
       v
 Local Repository
       |
       | git push
       v
 Remote Repository (GitHub)
```

## 5. Understanding the Three Main States

### A. Modified

The **modified state** means you have changed a file in your working directory.

For example, you edit `README.md` and add a new paragraph.

Git can detect that a tracked file has changed, but the changes are not yet staged.

Check the status using:

```bash
git status
```

### B. Staged

The **staged state** means you have selected changes to include in your next commit.

Use `git add` to stage a file:

```bash
git add README.md
```

You can stage a new file or changes to an existing tracked file.

Staging gives you control over which changes will be included in the next commit.

### C. Committed

The **committed state** means the staged changes have been saved as a snapshot in your local Git repository.

Use `git commit`:

```bash
git commit -m "Update README"
```

The `-m` option allows you to provide a commit message describing the changes.

A commit records a snapshot and metadata in the local repository. It does not automatically upload your changes to GitHub.

## 6. What Is a Remote Repository?

A **remote repository** is a version of your repository hosted elsewhere, commonly on GitHub.

Your local repository and remote repository can contain different commits until you synchronize them.

### `git push`

Uploads your local commits to a remote repository:

```bash
git push
```

### `git fetch`

Downloads information about new commits and references from a remote repository without automatically merging those changes into your current branch:

```bash
git fetch
```

### `git pull`

Fetches remote changes and integrates them into your current branch, typically using merge or rebase depending on your configuration:

```bash
git pull
```

### `git checkout`

Can switch between branches or restore files, depending on how it is used.

For switching branches, modern Git also provides:

```bash
git switch main
```

## 7. A Practical Example

Suppose you create a new file called `notes.md` inside your repository.

### Step 1: Create the file

```bash
touch notes.md
```

### Step 2: Check the repository status

```bash
git status
```

Git should report `notes.md` as an untracked file.

### Step 3: Stage the file

```bash
git add notes.md
```

### Step 4: Commit the change

```bash
git commit -m "Add Git workflow notes"
```

### Step 5: Push the commit to GitHub

```bash
git push
```

Your committed change is now uploaded to the remote repository, assuming your remote and authentication are configured correctly.

## 8. Essential Git Commands

| Command | Purpose |
|---|---|
| `git init` | Initializes a Git repository. |
| `git clone URL` | Creates a local copy of a remote repository. |
| `git status` | Shows the current state of the working directory and staging area. |
| `git add filename` | Stages a file's changes. |
| `git commit -m "message"` | Saves staged changes as a local commit. |
| `git push` | Uploads local commits to a remote repository. |
| `git fetch` | Retrieves remote updates without integrating them into the current branch. |
| `git pull` | Retrieves and integrates remote updates. |
| `git log` | Displays commit history. |
| `git diff` | Shows unstaged changes to tracked files. |
| `git diff --staged` | Shows staged changes. |

## 9. Key Takeaways

- Git tracks changes to files and records commits.
- GitHub hosts Git repositories online and provides collaboration tools.
- The `.git` directory stores the metadata needed for Git version control.
- `git status` helps you understand the current state of your work.
- `git add` stages changes.
- `git commit` saves a snapshot locally.
- `git push` uploads local commits to a remote repository.
- `git fetch` retrieves remote information; `git pull` also integrates changes.
- Committing and pushing are separate operations.

## 10. Knowledge Check

1. What is the difference between Git and GitHub?
2. What information does the `.git` directory store?
3. What is the purpose of the staging area?
4. What is the difference between `git add` and `git commit`?
5. Does `git commit` automatically upload your changes to GitHub?
6. What is the difference between `git fetch` and `git pull`?
7. Which command shows the current state of your repository?
