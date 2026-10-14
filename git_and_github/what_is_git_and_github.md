# What Is Git and GitHub?

## 1. What Is Version Control?

**Version control** is a system for tracking changes to files over time. It allows developers to record modifications, review previous versions, collaborate with others, and recover earlier work when necessary.

### Why Is Version Control Important?

Imagine you are building a website. You make changes to the layout, add features, and fix bugs. Later, you discover that one of your changes broke something.

Without version control, you might struggle to recover the previous working version.

With version control, you can:
- Track changes made to files.
- See who made changes and when.
- Compare different versions of your code.
- Restore previous versions when needed.
- Work on new features without immediately changing the main version.
- Collaborate with other developers.

**Example:** When a mobile app receives an update, its developers have usually changed code, fixed bugs, or introduced features. Version control helps developers manage and track those changes during development.

---

## 2. What Is Git?

**Git is a free, open-source, distributed version control system (DVCS)** used to track changes to files and coordinate development work.

Git was created by **Linus Torvalds** in 2005 to support the development of the Linux kernel.

### What Does Git Do?

Git allows developers to:
- Track changes in a project.
- Save snapshots of a project's state using commits.
- Compare changes between versions.
- Create branches to work on separate features.
- Merge changes from different branches.
- Work locally without requiring an internet connection for normal version-control operations.

### Important Git Terminology

| Term | Definition |
|---|---|
| Repository (repo) | A project tracked by Git, including its history |
| Commit | A recorded snapshot of changes |
| Branch | A separate line of development |
| Merge | Combining changes from different branches |
| Working directory | The files and folders you are currently working on |
| Staging area | The area where you select changes for the next commit |
| Git history | The recorded sequence of commits in a repository |

### Basic Git Workflow

A typical workflow is:

1. Modify files in your project.
2. Stage the changes you want to record.
3. Commit the staged changes.
4. Push commits to a remote repository if you want to share or back them up remotely.

Example:

```bash
git status
git add README.md
git commit -m "Update README"
git push
```

**Explanation:**
- `git status` shows the current state of your working directory and staging area.
- `git add README.md` stages changes to the specified file.
- `git commit -m "Update README"` records the staged changes in your local Git history.
- `git push` sends local commits to a configured remote repository.

Note that `git push` requires a configured remote and suitable access permissions.

---

## 3. What Is GitHub?

**GitHub is an online platform for hosting Git repositories and collaborating on software projects.**

It uses Git for version control and provides additional tools that support software development.

GitHub is not Git itself. Git can work without GitHub, but GitHub uses Git to manage repository history.

### What Does GitHub Provide?

GitHub offers features such as:

- **Repository hosting:** Store Git repositories online.
- **Pull requests:** Propose changes and request that they be reviewed and merged.
- **Access control:** Manage who can view or modify repositories.
- **Issues:** Track bugs, tasks, and feature requests.
- **Code reviews:** Discuss and review proposed changes.
- **GitHub Actions:** Automate workflows, such as running tests and building software.
- **Documentation:** Store project documentation, commonly in Markdown files.
- **Open-source collaboration:** Allow developers around the world to contribute to public projects.

### Public and Private Repositories

**Public repository**
- Visible to the public.
- Can allow contributions from external developers, subject to the project's contribution rules and permissions.

**Private repository**
- Access is restricted to authorized users.
- Useful for private projects, personal work, and company code.

---

## 4. Git vs GitHub

| Feature | Git | GitHub |
|---|---|---|
| What is it? | Version control system | Online development and repository-hosting platform |
| Main purpose | Track changes and manage project history | Host repositories and support collaboration |
| Where does it operate? | Commonly on your local computer; can also interact with remote repositories | Primarily through an online service |
| Requires internet? | Not for normal local operations | Internet is generally needed to use its hosted service |
| Tracks commits? | Yes | Displays and hosts Git commit history |
| Supports branches? | Yes | Provides an interface for branches and pull requests |
| Pull requests and code reviews? | Not built into core Git | Yes |
| Automation? | Can run scripts and hooks | Provides GitHub Actions and integrations |

**Remember:** Git is the version control tool; GitHub is a platform that hosts Git repositories and adds collaboration features.

---

## 5. How Git and GitHub Work Together

Consider a project where you are developing a website.

1. You create a project folder on your computer.
2. You initialize a Git repository.
3. You create and modify files.
4. You stage and commit your changes with Git.
5. You create or connect to a GitHub repository.
6. You push your commits to GitHub.
7. Other developers can review your work or collaborate, depending on repository permissions.

### Example Workflow

```bash
git init
git add .
git commit -m "Initial project setup"
git remote add origin YOUR_REPOSITORY_URL
git push -u origin main
```

**What these commands do:**
- `git init` initializes a Git repository in the current directory.
- `git add .` stages changes in the current directory and its subdirectories, subject to Git's ignore rules.
- `git commit` records the staged changes.
- `git remote add origin ...` adds a remote repository named `origin`.
- `git push -u origin main` pushes the `main` branch and sets its upstream branch.

Replace `YOUR_REPOSITORY_URL` with your actual GitHub repository URL. The remote repository must exist, and authentication and branch setup must be correct.

---

## 6. Benefits of Git

- **History:** Track how a project evolves over time.
- **Recovery:** Return to earlier committed versions when necessary.
- **Branching:** Develop features separately from the main line of development.
- **Collaboration:** Combine work from multiple contributors.
- **Performance:** Most Git operations are local and efficient.
- **Distributed design:** Each clone normally contains the repository's full history.
- **Open source:** Git is free to use and its source code is publicly available.

## 7. Benefits of GitHub

- **Remote hosting:** Keep a copy of your repository online.
- **Collaboration:** Work with developers in different locations.
- **Code review:** Use pull requests to discuss changes before merging.
- **Project management:** Track bugs, tasks, and feature requests with issues.
- **Automation:** Run tests and other development tasks with GitHub Actions.
- **Portfolio:** Showcase projects and demonstrate your skills to potential employers.
- **Open source:** Discover projects and contribute to other developers' work.

---

## 8. Common Misconceptions

1. **Git and GitHub are the same thing.**  
   Incorrect. Git is the version control system; GitHub is an online platform that uses Git.

2. **You need an internet connection to use Git.**  
   Incorrect. You can create repositories, commit changes, inspect history, and create branches locally without internet access.

3. **A commit automatically uploads code to GitHub.**  
   Incorrect. A commit saves changes to local Git history. You usually need `git push` to upload commits to a remote repository.

4. **GitHub is only for professional developers.**  
   Incorrect. Beginners can use GitHub to learn, document their progress, build projects, and contribute to open-source software.

5. **Every GitHub repository is public.**  
   Incorrect. GitHub supports both public and private repositories.

---

## 9. Knowledge Check

Try answering these questions without looking at the notes.

1. What is version control?
2. What is Git, and what problem does it solve?
3. Who created Git, and why?
4. What is GitHub?
5. State three differences between Git and GitHub.
6. What is a Git repository?
7. What does a commit record?
8. What is the difference between `git commit` and `git push`?
9. What is the difference between a public and a private repository?
10. Name three GitHub features that support collaboration.
11. Why might a developer create a branch?
12. Can you use Git without GitHub? Explain your answer.

## 10. Key Takeaways

- Version control tracks changes to files over time.
- Git is a distributed version control system.
- GitHub hosts Git repositories online and adds collaboration tools.
- Commits record changes locally; pushing shares commits with a remote.
- Branches allow separate lines of development.
- Pull requests support review and discussion before changes are merged.
- Git and GitHub are important tools for software development, collaboration, and building a technical portfolio.
