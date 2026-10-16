# GitHub: Branches

## 1. What Is a Branch?

A **branch** is an independent line of development within a Git repository. It allows developers to work on features or bug fixes without directly changing the `main` branch.

Branches help teams:
- Develop features independently.
- Fix bugs without disrupting other work.
- Review changes before merging them.
- Reduce conflicts when collaborating.

## 2. Check Your Repository

Before creating a branch, make sure you are in the correct directory and check the repository status.

```bash
pwd
git status
```

- `pwd` — displays your current working directory.
- `git status` — shows your current branch and whether you have uncommitted changes.

**Best practice:** Commit or safely store your existing changes before switching branches.

## 3. Create a Branch

There are two common ways to create a branch.

**Option 1: Create and switch to a new branch**

```bash
git checkout -b feature/lesson
```

This creates the `feature/lesson` branch and switches to it.

**Option 2: Create a branch without switching**

```bash
git branch feature/lesson
```

To switch to the new branch:

```bash
git checkout feature/lesson
```

You can also use the modern `git switch` commands:

```bash
git switch -c feature/lesson
git switch main
```

## 4. View Your Branches

```bash
git branch
```

This lists your local branches. An asterisk (`*`) identifies the branch you are currently using.

To see your current branch and working-tree status:

```bash
git status
```

**Important:** Changes committed on one branch do not automatically appear on another branch. They must be merged or otherwise incorporated.

## 5. Make Changes and Commit Them

After switching to your feature branch, create or edit a file.

For example, create a file named `test2.txt`:

```bash
touch test2.txt
```

Stage and commit the file:

```bash
git add test2.txt
git commit -m "Add test2 file"
```

- `git add` — stages changes for the next commit.
- `git commit` — records the staged changes in the local repository.

## 6. Push the Branch to GitHub

Upload your branch to the remote repository:

```bash
git push -u origin feature/lesson
```

- `git push` — uploads commits to a remote repository.
- `origin` — the conventional name for the remote repository.
- `feature/lesson` — the branch being pushed.
- `-u` — sets the upstream tracking relationship between the local branch and its remote counterpart.

After the upstream is configured, you can usually use:

```bash
git push
git pull
```

**Note:** `git push -u` does not make `origin` stop referring to your remote repository. It configures tracking for the specified branch.

## 7. Create a Pull Request (PR)

A **pull request** is a request to merge changes from one branch into another, usually through GitHub.

Typical workflow:

1. Push your feature branch to GitHub.
2. Open the repository on GitHub.
3. Select **Compare & pull request**.
4. Check the source branch and target branch.
5. Review the changes and write a description.
6. Click **Create pull request**.
7. Request a review from teammates.
8. Address feedback and resolve any issues.
9. Merge the pull request once the required checks and approvals are satisfied.

For example:

- **Source branch:** `feature/lesson`
- **Target branch:** `main`

The pull request displays the differences between these branches so reviewers can inspect the proposed changes.

### Why Are Pull Requests Important?

Pull requests allow teams to:
- Review code before merging.
- Identify bugs and potential improvements.
- Run automated tests and other quality checks.
- Discuss changes and request revisions.
- Maintain a more reliable `main` branch.

## 8. Branch Naming Conventions

Teams often use prefixes to identify the purpose of a branch.

| Prefix | Purpose | Example |
|---|---|---|
| `feature/` | New functionality | `feature/search-bar` |
| `fix/` | Bug fixes | `fix/login-error` |
| `docs/` | Documentation changes | `docs/readme-update` |
| `test/` | Testing-related work | `test/login-tests` |

Follow the naming conventions used by your project or team.

## 9. Merge a Pull Request

After the pull request has been reviewed and approved, it can be merged into the target branch.

On GitHub:

1. Open the pull request.
2. Confirm that the required reviews and checks have passed.
3. Click **Merge pull request** or the available merge option.
4. Confirm the merge if prompted.

GitHub may offer the option to delete the feature branch after merging.

Deleting a merged branch is often good practice because it keeps the repository organized. You can keep it if your workflow requires it.

## 10. Update Your Local Main Branch

After merging the pull request on GitHub, update your local repository.

```bash
git switch main
git pull
```

- `git switch main` — switches to your local `main` branch.
- `git pull` — fetches and integrates changes from the configured upstream branch.

Check the files in your current directory:

```bash
ls
```

On Windows Command Prompt, you can use:

```cmd
dir
```

The merged file, such as `test2.txt`, should now be available in your local `main` branch if it was included in the merge.

You can verify your repository status:

```bash
git status
```

## 11. Complete Branching Workflow

The typical feature-branch workflow is:

```text
1. Check repository status
        ↓
2. Create a feature branch
        ↓
3. Make changes
        ↓
4. Stage and commit changes
        ↓
5. Push the branch to GitHub
        ↓
6. Create a pull request
        ↓
7. Review and test changes
        ↓
8. Merge into main
        ↓
9. Switch to local main
        ↓
10. Pull the latest changes
```

## Key Takeaways

- A branch isolates work from other branches.
- `git checkout -b` creates and switches to a branch.
- `git branch` lists local branches or creates one when given a name.
- `git add` stages changes, while `git commit` records them.
- `git push` uploads commits to a remote repository.
- `git push -u` configures upstream tracking for a branch.
- A pull request allows changes to be reviewed before merging.
- Merging incorporates changes from one branch into another.
- `git pull` updates the current branch from its configured upstream.
- Feature branches make collaboration safer and more manageable.

## Commands to Remember

| Command | Purpose |
|---|---|
| `pwd` | Show the current directory |
| `git status` | Check repository status |
| `git branch` | List local branches |
| `git branch feature/name` | Create a branch |
| `git checkout -b feature/name` | Create and switch branches |
| `git switch main` | Switch to `main` |
| `git add filename` | Stage a file |
| `git commit -m "message"` | Commit staged changes |
| `git push -u origin feature/name` | Push a branch and set upstream tracking |
| `git pull` | Fetch and integrate upstream changes |
| `ls` | List directory contents |

