# Forking in GitHub

## 1. What Is Forking?

**Forking** is the process of creating a copy of another user's repository under your own GitHub account.

A fork allows you to experiment with code, make changes, and contribute to projects without modifying the original repository.

### Why Use Forking?

- Contribute to open-source projects.
- Experiment with code without affecting the original project.
- Develop new features independently.
- Fix bugs and propose improvements.
- Submit changes to the original repository using a Pull Request (PR).

## 2. Forking vs. Branching

The main difference is where the new copy or development work exists.

| Feature | Forking | Branching |
|---|---|---|
| Location | Creates a separate repository under your GitHub account. | Creates a separate branch within the same repository. |
| Common use | Contributing to projects you do not own. | Developing features within a shared repository. |
| Independence | You can work independently of the original repository. | Branches belong to the same repository. |
| Sharing changes | Usually through a Pull Request between repositories. | Usually through a Pull Request between branches. |

**Remember:**
- A **fork** is a separate repository.
- A **branch** is a separate line of development within a repository.

## 3. How Forking Works

Imagine a developer named Joe wants to contribute to a repository called `coolgame`.

1. The original owner maintains the `coolgame` repository.
2. Joe forks the repository into his own GitHub account.
3. Joe clones his fork to his local computer.
4. Joe creates a branch and makes changes.
5. Joe pushes his branch to his fork on GitHub.
6. Joe opens a Pull Request against the original repository.
7. The original owner reviews the changes and decides whether to merge them.

This workflow allows Joe to contribute without directly modifying the original repository.

### Understanding the Repositories

- **Original repository (upstream):** The project maintained by its original owner.
- **Forked repository (origin):** Your personal copy of the original project on GitHub.
- **Local repository:** The copy stored on your computer.

When you clone your fork, Git normally names the fork's remote `origin`. The original repository can be added as another remote, commonly called `upstream`.

## 4. How to Fork a Repository on GitHub

For practice, use GitHub's example repository: [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife).

**Step 1:** Open the repository on GitHub.

**Step 2:** Click the **Fork** button.

**Step 3:** Select your personal GitHub account as the destination.

**Step 4:** Confirm the fork creation if prompted.

GitHub creates a separate repository under your account.

### How to Identify a Fork

On your fork's repository page, GitHub displays information indicating that it was forked from the original repository.

Depending on the current interface, you may also see options such as **Sync fork** to bring changes from the original repository into your fork.

**Important:** GitHub does not allow you to fork a repository you already own. Fork a repository owned by another account to practise this workflow.

## 5. Working with Your Fork Locally

After creating your fork, you can clone it to your computer and make changes.

### Step 1: Clone Your Fork

Copy the URL of your fork from your GitHub account.

```bash
git clone <your-forked-repo-url>
```

**Important:** Use the URL of your fork, not the original owner's repository.

### Step 2: Navigate into the Repository

```bash
cd Spoon-Knife
```

### Step 3: Create and Switch to a New Branch

```bash
git switch -c test/forking-example
```

This creates a new branch and switches to it.

The branch name `test/forking-example` is used for this example.

### Step 4: Create a File

```bash
touch text.txt
```

This creates an empty file named `text.txt`.

Add some content to the file before committing if you want to practise making a meaningful change.

### Step 5: Stage and Commit Your Changes

Stage the file:

```bash
git add text.txt
```

Commit the staged changes:

```bash
git commit -m "chore: testing"
```

A commit records your changes in the local repository.

### Step 6: Push Your Branch to GitHub

```bash
git push -u origin test/forking-example
```

Explanation:

- `git push` uploads your local commits to a remote repository.
- `-u` sets the upstream tracking relationship for the branch.
- `origin` refers to your fork by default.
- `test/forking-example` is the branch being pushed.

Once pushed, your branch will be available in your fork on GitHub.

## 6. Creating a Pull Request

A **Pull Request (PR)** proposes changes for review before they are merged into another branch or repository.

### Step 1: Open Your Fork on GitHub

Navigate to your fork after pushing your branch.

### Step 2: Click "Compare & pull request"

GitHub may display a **Compare & pull request** button for your recently pushed branch.

If it does not appear:

1. Open the **Pull requests** tab.
2. Click **New pull request**.
3. Select the appropriate source and destination repositories and branches.

### Step 3: Check the Comparison

For a contribution to the original repository, the comparison should generally be:

- **Base repository:** The original project.
- **Base branch:** The branch you want to merge into, often `main`.
- **Head repository:** Your fork.
- **Compare branch:** Your feature branch, such as `test/forking-example`.

Check these selections carefully before creating the PR.

### Step 4: Create the Pull Request

Provide a clear title and description explaining your changes, then submit the PR.

The original project's maintainers can review your contribution, request changes, approve it, and merge it if they choose.

**Remember:** Opening a PR does not automatically merge your changes.

## 7. Keeping Your Fork Up to Date

The original repository may receive new commits after you fork it.

To keep your fork up to date, you can use GitHub's **Sync fork** feature or configure an `upstream` remote and fetch changes through Git.

### Add the Original Repository as Upstream

From your local repository:

```bash
git remote add upstream <original-repo-url>
```

Example:

```bash
git remote add upstream https://github.com/octocat/Spoon-Knife.git
```

Check your configured remotes:

```bash
git remote -v
```

You should see your fork as `origin` and the original repository as `upstream`.

### Fetch Changes from the Original Repository

```bash
git fetch upstream
```

This downloads information about the original repository's branches and commits without automatically merging them into your current branch.

To update your local `main` branch with the original repository's `main` branch, switch to `main` and merge the fetched changes:

```bash
git switch main
git merge upstream/main
```

You can then push the updated branch to your fork if needed:

```bash
git push origin main
```

**Note:** These commands assume the original repository uses a `main` branch and that your local branch is configured appropriately. Resolve any merge conflicts if they occur.

## 8. Contribution Guidelines

Before submitting a Pull Request to an open-source project, look for a file named `CONTRIBUTING.md`.

It may explain:

- How to report bugs and suggest features.
- Coding standards and formatting rules.
- Testing requirements.
- Branch naming conventions.
- Commit message conventions.
- Pull Request expectations.

Following these guidelines makes your contribution easier for maintainers to review.

## 9. Key Takeaways

- Forking creates a separate repository under your GitHub account.
- Branching creates a separate line of development within a repository.
- You can modify your fork without directly changing the original project.
- Clone your fork to work on it locally.
- Create a branch to organize your changes.
- Use `git add`, `git commit`, and `git push` to publish your work.
- Submit a Pull Request to propose your changes to the original repository.
- Keep your fork updated with changes from the original repository.
- Always check the project's contribution guidelines before submitting a PR.

## 10. Practice Exercise

Practise the complete forking workflow using [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife).

- Fork the repository to your GitHub account.
- Clone your fork to your computer.
- Create a branch named `test/forking-example`.
- Create a file named `text.txt`.
- Stage and commit the file.
- Push the branch to your fork.
- Open a Pull Request against the original repository.
- Identify the base repository and head repository in the PR.

**Goal:** Understand how to contribute to a project on GitHub without needing direct write access to its original repository.