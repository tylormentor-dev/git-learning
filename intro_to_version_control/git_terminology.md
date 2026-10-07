# GitHub Terminology

## 1. Git

**Git** is a distributed version control system used to track changes to files, especially source code.

Git runs locally on your computer.

Example:

```bash
git status
git add .
git commit -m "Add notes"
```

---

## 2. GitHub

**GitHub** is a cloud-based platform for hosting Git repositories and collaborating with other developers.

Git and GitHub are not the same thing.

* **Git** = version control software
* **GitHub** = online platform for hosting and collaborating on Git repositories

---

## 3. Repository (Repo)

A **repository** is a project managed by Git.

It contains:

* Source code
* Files
* Git history
* Branches
* Commits

Example:

```text
my-project/
├── README.md
├── app.py
└── .git/
```

---

## 4. Local Repository

A **local repository** is the Git repository stored on your computer.

Example:

```text
C:\Users\Tylor\Documents\Coding\my-project
```

You can work on it without being connected to GitHub.

---

## 5. Remote Repository

A **remote repository** is a repository stored somewhere other than your local computer.

GitHub repositories are commonly used as remote repositories.

Example:

```text
Local computer  →  GitHub
```

---

## 6. Clone

**Cloning** means copying an existing GitHub repository to your computer.

Command:

```bash
git clone https://github.com/username/repository.git
```

After cloning, you have a local copy of the repository.

---

## 7. Commit

A **commit** is a saved snapshot of changes in your Git repository.

Example:

```bash
git commit -m "Add Git notes"
```

The commit message describes what changed.

Think of a commit as a checkpoint in your project.

---

## 8. Commit Message

A **commit message** explains what a commit changed.

Example:

```bash
git commit -m "Add Git branching notes"
```

Good commit messages should be clear and specific.

Bad:

```bash
git commit -m "stuff"
```

Better:

```bash
git commit -m "Add notes about Git branches"
```

---

## 9. Working Directory

The **working directory** is the files you are currently working on.

For example, if you edit:

```text
README.md
app.py
```

those changes exist in your working directory before being committed.

---

## 10. Staging Area

The **staging area** contains changes that you have selected to include in your next commit.

Example:

```bash
git add README.md
```

Now `README.md` is staged.

You can check this with:

```bash
git status
```

---

## 11. `git add`

`git add` moves changes into the staging area.

Add one file:

```bash
git add README.md
```

Add multiple files:

```bash
git add README.md app.py
```

Add everything:

```bash
git add .
```

---

## 12. `git status`

`git status` shows the current state of your repository.

It can tell you about:

* Modified files
* Untracked files
* Staged files
* Uncommitted changes
* Your current branch

Command:

```bash
git status
```

This is one of the most important Git commands to learn.

---

## 13. Push

**Push** sends your local commits to a remote repository such as GitHub.

```bash
git push
```

Example:

```text
Your computer
     ↓
   git push
     ↓
   GitHub
```

---

## 14. Pull

**Pull** downloads changes from a remote repository and integrates them into your local repository.

```bash
git pull
```

Example:

```text
GitHub
   ↓
git pull
   ↓
Your computer
```

---

## 15. Fetch

**Fetch** downloads information about changes from the remote repository without automatically integrating those changes into your current branch.

```bash
git fetch
```

A useful distinction:

```text
git fetch = download information
git pull  = fetch + integrate changes
```

---

# Branches

## 16. Branch

A **branch** is an independent line of development.

The default branch is commonly called:

```text
main
```

You can create another branch:

```bash
git branch feature-login
```

Branches allow developers to work on features without immediately changing the main codebase.

---

## 17. Main Branch

The **main branch** is commonly the primary branch of a repository.

Example:

```text
main
```

It generally contains the stable or production-ready version of the project.

---

## 18. Feature Branch

A **feature branch** is created to work on a particular feature.

Example:

```bash
git checkout -b feature-login
```

or:

```bash
git switch -c feature-login
```

Example workflow:

```text
main
 │
 └── feature-login
       │
       ├── changes
       ├── commits
       └── testing
```

---

## 19. Checkout

`git checkout` can be used to switch branches and perform other Git operations.

Example:

```bash
git checkout main
```

Switches to the `main` branch.

Modern Git also provides:

```bash
git switch main
```

which is specifically designed for switching branches.

---

## 20. Merge

**Merging** combines changes from one branch into another branch.

Example:

```bash
git switch main
git merge feature-login
```

This combines the `feature-login` branch with `main`.

---

## 21. Merge Conflict

A **merge conflict** occurs when Git cannot automatically determine which changes should be kept.

For example, two developers modify the same part of a file differently.

Git may show:

```text
Your changes
```

You must manually decide which version to keep.

---

# GitHub Collaboration

## 22. Fork

A **fork** is your own copy of another person's GitHub repository under your GitHub account.

Forks are commonly used when contributing to open-source projects.

Example:

```text
Original Repository
        ↓
      Fork
        ↓
Your GitHub Repository
```

---

## 23. Pull Request (PR)

A **Pull Request** is a request to merge changes from one branch/repository into another.

For example:

```text
feature-login
      ↓
Pull Request
      ↓
main
```

Other developers can review your changes before they are merged.

---

## 24. Code Review

**Code review** is the process of examining someone's code before it is merged.

Developers may:

* Comment on code
* Suggest changes
* Ask questions
* Approve the changes
* Request changes

Code review is a major part of professional software development.

---

## 25. Approve

When reviewing a Pull Request, a developer can **approve** the changes.

Approval indicates that the reviewer is satisfied with the proposed changes.

---

## 26. Request Changes

A reviewer can **request changes** when modifications are needed before the Pull Request can be merged.

---

## 27. Issue

A **GitHub Issue** is used to track a problem, task, bug, feature request, or other piece of work.

Examples:

```text
Bug: Login button does not work

Feature: Add dark mode

Task: Update dependencies
```

---

## 28. Labels

**Labels** categorize Issues and Pull Requests.

Examples:

```text
bug
enhancement
documentation
help wanted
good first issue
```

---

## 29. Milestone

A **milestone** groups Issues and Pull Requests around a particular goal or release.

Example:

```text
Milestone: Version 2.0

- Fix login bug
- Add user profiles
- Add password reset
```

---

## 30. README

A `README.md` file explains what a repository is and how to use it.

A README commonly contains:

* Project description
* Installation instructions
* Usage instructions
* Technologies used
* Examples
* Contribution instructions

Example:

```text
README.md
```

---

# GitHub Permissions and Collaboration

## 31. Contributor

A **contributor** is someone who makes contributions to a repository.

Contributions can include:

* Code
* Documentation
* Bug fixes
* Tests
* Features

---

## 32. Collaborator

A **collaborator** is someone who has been given access to work directly on a repository.

---

## 33. Organization

A **GitHub Organization** is a shared account used by companies, teams, and open-source projects.

Instead of everything belonging to one person's account:

```text
Company
 ├── Repository A
 ├── Repository B
 └── Repository C
```

---

## 34. Repository Permissions

Repository permissions determine what someone is allowed to do.

Depending on their role, a person may be able to:

* Read
* Write
* Create branches
* Manage Issues
* Review Pull Requests
* Manage repository settings

---

# GitHub Actions and Automation

## 35. GitHub Actions

**GitHub Actions** is GitHub's automation and CI/CD platform.

It can automatically:

* Run tests
* Build applications
* Check code
* Deploy applications
* Run security checks

Example:

```text
Developer pushes code
        ↓
GitHub Actions
        ↓
Run tests
        ↓
Build application
        ↓
Deploy
```

---

## 36. Workflow

A **workflow** is an automated process defined for GitHub Actions.

Workflow files are usually stored in:

```text
.github/workflows/
```

Example:

```text
.github/
└── workflows/
    └── tests.yml
```

---

## 37. CI — Continuous Integration

**Continuous Integration (CI)** means regularly integrating code changes and automatically checking them.

For example:

```text
Developer pushes code
        ↓
Run automated tests
        ↓
Check code
        ↓
Report result
```

---

## 38. CD — Continuous Delivery / Deployment

**Continuous Delivery/Deployment** involves automatically preparing or deploying software after changes pass the required checks.

Example:

```text
Push code
   ↓
Tests
   ↓
Build
   ↓
Deploy
```

---

# GitHub Releases and Versions

## 39. Release

A **GitHub Release** represents a specific version of a project.

Example:

```text
v1.0.0
v1.1.0
v2.0.0
```

Releases are commonly associated with Git tags.

---

## 40. Tag

A **tag** identifies a specific commit.

Example:

```bash
git tag v1.0.0
```

Tags are commonly used to mark versions.

---

# Important Git Concepts

## 41. HEAD

`HEAD` represents your current position in the Git history.

Usually, it points to the commit you currently have checked out.

Example:

```text
HEAD
 ↓
main
 ↓
Latest commit
```

---

## 42. Repository History

Git stores the history of commits made to a repository.

You can view it with:

```bash
git log
```

A shorter version:

```bash
git log --oneline
```

---

## 43. Remote

A **remote** is a reference to another repository.

A common remote name is:

```text
origin
```

You can see your remotes with:

```bash
git remote -v
```

---

## 44. Origin

`origin` is the conventional name Git gives to the remote repository when you clone a repository.

Example:

```bash
git push origin main
```

This means:

```text
Push my local main branch
        ↓
to the remote called origin
        ↓
into its main branch
```

---

## 45. Upstream

**Upstream** can refer to the branch or repository that your current branch is tracking.

For example:

```text
local main
     ↓
tracks
     ↓
origin/main
```

This makes commands such as:

```bash
git pull
git push
```

simpler because Git knows which remote branch to use.

---

# Important GitHub Development Terms

## 46. Open Source

**Open-source software** has source code that is made available for others to inspect, use, modify, and potentially contribute to, subject to its license.

GitHub hosts many open-source projects.

---

## 47. Contribution

A **contribution** is work you make to a project.

Examples:

* Creating code
* Fixing bugs
* Improving documentation
* Adding tests
* Reviewing Pull Requests
* Reporting bugs
* Improving examples

---

## 48. GitHub Contribution Graph

Your GitHub profile contains a contribution graph showing activity associated with your account.

Contributions can come from activities such as commits, Pull Requests, Issues, and other qualifying activity.

---

## 49. `.gitignore`

A `.gitignore` file tells Git which files or folders should not be tracked.

Example:

```text
.env
__pycache__/
node_modules/
*.log
```

This is particularly important for preventing sensitive files such as environment variables from being committed.

---

## 50. Environment Variables

Environment variables store configuration values outside your source code.

Example:

```text
API_KEY
DATABASE_URL
PASSWORD
```

Sensitive values should generally **not** be committed directly to GitHub.

---

# Professional GitHub Workflow

A common professional workflow looks like:

```text
Create Issue
     ↓
Create Feature Branch
     ↓
Write Code
     ↓
Test Code
     ↓
git add
     ↓
git commit
     ↓
git push
     ↓
Create Pull Request
     ↓
Code Review
     ↓
Fix Requested Changes
     ↓
Approval
     ↓
Merge
     ↓
Delete Feature Branch
```

## Example

```bash
git switch main

git pull

git switch -c feature-login

# Make changes

git status

git add .

git commit -m "Add login functionality"

git push -u origin feature-login
```

Then create a **Pull Request** on GitHub.

After review and approval, the branch can be merged into `main`.

---

# Commands I Need to Know

```bash
git init
git clone
git status
git add
git commit
git log
git branch
git switch
git merge
git fetch
git pull
git push
git remote
git restore
git reset
git diff
git stash
git tag
```

# GitHub Concepts I Need to Know

* Git
* GitHub
* Repository
* Local repository
* Remote repository
* Clone
* Commit
* Working directory
* Staging area
* Branch
* Main branch
* Feature branch
* Merge
* Merge conflict
* Pull Request
* Fork
* Issue
* Code review
* Contributor
* Collaborator
* Organization
* README
* `.gitignore`
* GitHub Actions
* Workflow
* CI/CD
* Release
* Tag
* Open source
* Contribution
* Contribution graph
* Environment variables
* Repository permissions
