# GitHub: Workflows

## 1. What Is a Workflow?

A **workflow** is a sequence of steps followed to complete a task.

In software development, a workflow provides a consistent process for writing, testing, reviewing, and sharing code with other developers.

A good workflow helps teams:
- Organize development tasks.
- Collaborate without interfering with each other's work.
- Identify bugs before changes are merged.
- Maintain code quality.
- Reduce conflicts and deployment problems.

The workflow a team chooses depends on factors such as team size, project requirements, and development practices.

## 2. Common Git Workflows

### Feature Branch Workflow

Developers create separate branches for individual features or bug fixes. Once the work is complete, they open a pull request for review before merging their changes into `main`.

### Centralized Workflow

Developers work directly with a shared main branch in a centralized repository. This approach is simple but can increase the risk of conflicting changes when several developers work together.

### Gitflow Workflow

A branching model that uses dedicated branches for development, features, releases, and urgent fixes. It can be useful for projects with structured release cycles but may be unnecessarily complex for smaller projects.

## 3. Feature Branch Workflow

The **feature branch workflow** is a common approach to collaborative development.

Instead of making changes directly to `main`, a developer creates a separate branch for a task.

The `main` branch remains unchanged until the feature branch has been reviewed and merged.

### How It Works

1. Get the latest code from the remote repository.
2. Create a new feature branch.
3. Make changes to the code.
4. Stage and commit the changes.
5. Push the branch to GitHub.
6. Create a pull request.
7. Review and test the changes.
8. Merge the branch into `main`.

## 4. Step-by-Step Feature Branch Workflow

### Step 1 — Update Your Local Repository

Before starting new work, switch to `main` and pull the latest changes.

```bash
git switch main
git pull origin main
```

- `git switch main` — switches to the local `main` branch.
- `git pull origin main` — fetches and integrates changes from the remote `main` branch.

### Step 2 — Create a Feature Branch

Create a new branch and switch to it.

```bash
git switch -c feature/readme-update
```

The branch `feature/readme-update` is now your working branch.

You can verify your current branch using:

```bash
git branch
```

### Step 3 — Make Changes

Create or edit a file. For example, create a `README.md` file:

```bash
touch README.md
```

A `README.md` file typically explains what a project does, how to install it, and how to use it.

**Note:** If the file already exists, edit it instead of creating another one.

### Step 4 — Stage Your Changes

Stage the file so Git knows which changes to include in the next commit.

```bash
git add README.md
```

To stage all changes in the current directory and its subdirectories:

```bash
git add .
```

Use `git status` to check which files are staged, modified, or untracked.

### Step 5 — Commit Your Changes

Create a commit with a clear, meaningful message.

```bash
git commit -m "Update README documentation"
```

A commit records the staged changes in your local Git repository.

### Step 6 — Push Your Branch to GitHub

Upload your branch and its commits to the remote repository.

```bash
git push -u origin feature/readme-update
```

- `git push` — uploads commits to the remote repository.
- `origin` — the conventional name for the remote repository.
- `feature/readme-update` — the branch being pushed.
- `-u` — configures upstream tracking for future pushes and pulls.

After upstream tracking has been configured, you can generally use:

```bash
git push
```

**Important:** You push a branch and its commits, not an individual file.

### Step 7 — Create a Pull Request

Open your repository on GitHub and create a pull request.

A **pull request (PR)** proposes merging changes from one branch into another.

For example:

- **Source branch:** `feature/readme-update`
- **Target branch:** `main`

The pull request allows reviewers to inspect the changes, discuss improvements, and check whether the code meets the project's requirements.

### Step 8 — Review and Merge

During the review process, developers may:
- Approve the changes.
- Request changes.
- Identify bugs or improvements.
- Check automated tests and other quality requirements.

Once the necessary approvals and checks have passed, merge the pull request into `main`.

### Step 9 — Update Your Local Main Branch

After the pull request has been merged, update your local `main` branch.

```bash
git switch main
git pull origin main
```

Your local repository now includes the changes merged into the remote `main` branch.

## 5. Feature Branch Workflow Diagram

```text
Update local main
       |
       v
Create feature branch
       |
       v
Write or modify code
       |
       v
Stage and commit changes
       |
       v
Push branch to GitHub
       |
       v
Create pull request
       |
       v
Review and test changes
       |
       v
Merge into main
       |
       v
Update local main
```

## 6. Why Use a Workflow?

A consistent workflow makes collaboration easier because each developer understands how changes should be introduced into the project.

| Benefit | Explanation |
|---|---|
| Collaboration | Developers can work on separate tasks independently. |
| Code review | Changes can be checked before merging. |
| Quality control | Tests and review rules help identify problems. |
| Fewer disruptions | Developers avoid making every change directly on `main`. |
| Traceability | Commits and pull requests provide a record of changes. |
| Safer releases | Teams can validate changes before deploying them. |

## 7. Key Takeaways

- A workflow is a structured sequence of steps used to complete a task.
- Git workflows define how developers create, share, review, and merge changes.
- The feature branch workflow keeps new work separate from `main`.
- `git pull` updates your current branch from its configured remote branch.
- `git switch -c` creates a branch and switches to it.
- `git add` stages changes.
- `git commit` records staged changes locally.
- `git push` uploads commits to GitHub.
- A pull request enables review before merging.
- `git switch main` and `git pull origin main` help update your local `main` after a merge.

## Commands to Remember

| Command | Purpose |
|---|---|
| `git status` | Check repository status |
| `git switch main` | Switch to the main branch |
| `git pull origin main` | Update the current branch from remote `main` |
| `git switch -c feature/name` | Create and switch to a new branch |
| `git add README.md` | Stage a specific file |
| `git add .` | Stage changes in the current directory |
| `git commit -m "message"` | Record staged changes |
| `git push -u origin feature/name` | Push a branch and configure upstream tracking |
| `git push` | Push commits to the configured upstream |
