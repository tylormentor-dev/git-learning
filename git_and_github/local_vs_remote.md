# Remote vs Local in Git

## 1. What Is Local vs Remote?

### Local Repository

A **local repository** is the Git repository stored on your own computer.

You can:
- Create and edit files.
- Stage changes using `git add`.
- Save snapshots using `git commit`.
- Work offline and commit changes when you are ready.

### Remote Repository

A **remote repository** is a version of your repository hosted somewhere else, such as GitHub, or on another developer's machine.

You can:
- Share code with other developers.
- Push your local commits to the remote repository.
- Pull changes made by other developers.
- Collaborate on the same project.

A remote repository is accessed through a URL, also called a **URI**. Access may require appropriate permissions.

## 2. Local vs Remote: Key Differences

| Feature | Local Repository | Remote Repository |
|---|---|---|
| Location | Your computer | A remote server or another machine |
| Main purpose | Develop and save work locally | Share and synchronize work |
| `git commit` | Saves changes locally | Does not directly save changes remotely |
| `git push` | Sends local commits to a remote | Receives pushed commits |
| `git pull` | Retrieves and integrates remote changes | Provides changes to your local repository |
| Offline work | Yes | Usually requires a network connection to access |

## 3. Important Git Terminology

- **Repository (repo):** A location where Git tracks a project's files and history.
- **Clone:** Creates a local copy of a remote repository, including its Git history.
- **Push:** Sends local commits to a remote repository.
- **Pull:** Fetches remote changes and integrates them into the current local branch.
- **Remote URL:** The address used to connect to a remote repository.
- **`origin`:** The conventional default name for the remote created when you clone a repository. You can use other names.

## 4. How Local and Remote Work Together

A typical workflow looks like this:

1. Clone a repository from GitHub to your computer.
2. Edit files in your local working directory.
3. Stage the changes using `git add`.
4. Commit the changes using `git commit`.
5. Push the commits to GitHub using `git push`.
6. Other developers pull the latest changes to update their local repositories.

```text
Remote repository (GitHub)
          |
       git clone
          v
     Local repository
          |
    Edit files
          |
       git add
          |
      git commit
          |
       git push
          v
Remote repository (GitHub)
          |
       git pull
          v
Another developer's local repository
```

**Important:** Committing and pushing are different operations. A commit saves your work locally; a push sends committed changes to the remote.

## 5. Checking Your Remote Connection

### Check whether a remote is configured

```bash
git remote
```

This displays the names of your configured remotes.

If nothing is displayed, no remote is configured for that repository.

### Display remote names and URLs

```bash
git remote -v
```

The `-v` option means *verbose*. It displays the remote names and their URLs for fetching and pushing.

Example:

```text
origin  https://github.com/username/my-repo.git (fetch)
origin  https://github.com/username/my-repo.git (push)
```

### Add a remote repository

```bash
git remote add origin <REMOTE_URL>
```

Replace `<REMOTE_URL>` with the actual URL of your repository.

Example:

```bash
git remote add origin https://github.com/username/my-repo.git
```

This connects your local repository to a remote named `origin`. It does not automatically upload your files.

## 6. Creating and Connecting a Local Repository

The following commands create a new local repository:

```bash
mkdir my-second-repo
cd my-second-repo
git init
```

- `mkdir` creates a directory.
- `cd` enters the directory.
- `git init` initializes a Git repository inside it.

Check the configured remotes:

```bash
git remote -v
```

If the repository was just initialized, this will normally display nothing because a remote has not yet been configured.

You can connect it to a remote with:

```bash
git remote add origin <REMOTE_URL>
```

Then verify the connection:

```bash
git remote -v
```

## 7. Clone vs Pull

| Command | When to use it | What it does |
|---|---|---|
| `git clone <URL>` | When you need a local copy of a remote repository | Creates a local repository and configures its remote |
| `git pull` | When you already have a local repository and want remote changes | Fetches and integrates changes into the current branch |

You generally clone a repository the first time you want to work on it. Later, you pull changes to update your local branch.

## 8. Understanding Branches and Remote Tracking

Repositories can contain multiple branches. A remote may have a `main` branch, while your local repository may not yet have a corresponding local branch.

To see local and remote branches:

```bash
git branch
git branch -r
git branch -a
```

- `git branch` lists local branches.
- `git branch -r` lists remote-tracking branches.
- `git branch -a` lists both local and remote-tracking branches.

To create a local branch named `main` that tracks the remote's `main` branch, if needed:

```bash
git switch --track origin/main
```

If your local `main` branch already exists, switch to it with:

```bash
git switch main
```

**Note:** The lesson demonstrates `git checkout main`. The newer `git switch` command is often clearer when switching branches. The correct command depends on which branches already exist and whether they have been configured to track a remote branch.

## 9. Common Commands Reference

| Command | Purpose |
|---|---|
| `git status` | Shows the state of your working directory and staging area |
| `git remote` | Lists configured remote names |
| `git remote -v` | Lists remote names and URLs |
| `git remote add origin <URL>` | Adds a remote named `origin` |
| `git clone <URL>` | Copies a remote repository locally |
| `git pull` | Fetches and integrates remote changes |
| `git push` | Sends local commits to a remote |
| `git branch -a` | Lists local and remote-tracking branches |
| `git switch main` | Switches to the local `main` branch |

## 10. Key Takeaways

- **Local** means your repository on your own machine.
- **Remote** means a repository hosted somewhere else.
- You can work offline and commit changes locally.
- `git push` sends your commits to the remote repository.
- `git pull` retrieves and integrates remote changes.
- `git clone` is used to create a local copy of a remote repository.
- `origin` is a conventional remote name, not a special Git command.
- `git remote -v` helps you verify which remote URLs are configured.

## 11. Knowledge Check

Try answering these questions without looking at the notes:

1. What is the difference between a local and a remote repository?
2. What is the difference between `git commit` and `git push`?
3. When should you use `git clone` instead of `git pull`?
4. What does `git remote -v` display?
5. What does the name `origin` usually represent?
6. Why might another developer not see your latest local commit on GitHub?
7. What is the difference between a local branch and a remote-tracking branch?
