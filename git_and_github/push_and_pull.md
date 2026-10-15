# Push and Pull in Git

## 1. Overview

Git allows you to work on a project locally and synchronize your changes with a remote repository, such as GitHub.

- **`git push`** uploads local commits to a remote repository.
- **`git pull`** retrieves remote changes and integrates them into your current local branch.

Git is a distributed version control system, so you can make changes and commit them locally without being connected to GitHub.

## 2. Git Push

The `git push` command sends committed changes from your local repository to a remote repository.

### Check your repository status

```bash
git status
```

Example output:

```text
Your branch is ahead of 'origin/main' by 1 commit.
```

This means your local `main` branch contains one commit that has not yet been pushed to the remote `main` branch.

### Check your current branch

```bash
git branch
```

The asterisk (`*`) identifies the branch you are currently using.

### Push your changes

```bash
git push origin main
```

- `git push` sends local commits to a remote.
- `origin` is the name of the remote repository.
- `main` is the destination branch.

After a successful push, your commits are available on GitHub, provided the remote branch was updated successfully.

## 3. Git Pull

The `git pull` command retrieves changes from a remote repository and integrates them into your current local branch.

For example, another developer might update a file directly on GitHub. Your local copy will not automatically contain that update.

To retrieve it, run:

```bash
git pull
```

Git fetches the remote changes and integrates them into your current branch. If Git can combine the changes automatically, it does so. If conflicting changes cannot be resolved automatically, you must resolve the merge conflict.

### Example

Suppose `test.txt` contains no text in your local repository.

Another developer adds this line to `test.txt` on GitHub:

```text
This is my change.
```

After running:

```bash
git pull
```

The new line becomes available in your local file, assuming the pull completes successfully.

## 4. Push vs Pull

| Command | Direction | Purpose |
|---|---|---|
| `git push` | Local → Remote | Uploads local commits |
| `git pull` | Remote → Local | Retrieves and integrates remote changes |

## 5. Recommended Workflow

When working on a project, use this general workflow:

```bash
git status
git add .
git commit -m "Describe your changes"
git pull
git push
```

This workflow checks your status, stages changes, commits them locally, integrates remote changes, and then pushes your commits.

**Important:** If you have uncommitted changes, make sure they are safely saved before pulling. Git may stop the pull if your changes would be overwritten. Also, `git pull` can create conflicts that must be resolved before you can push.

For an existing project, checking for remote updates before pushing helps reduce avoidable push rejections.

## 6. Understanding Push Rejections

A push may be rejected if the remote branch contains commits that your local branch does not have.

For example:

1. Another developer pushes a commit to GitHub.
2. Your local branch has not received that commit.
3. You try to push your own commit.
4. Git rejects the push because the remote branch has moved ahead.

A common solution is:

```bash
git pull
```

Resolve any conflicts if necessary, complete the integration, and then run:

```bash
git push
```

Do not force-push as a routine fix, because it can overwrite remote history and disrupt other contributors.

## 7. Key Takeaways

- `git commit` saves a snapshot in your local repository.
- `git push` sends committed changes to a remote repository.
- `git pull` fetches and integrates remote changes into your current branch.
- Other developers' changes are not automatically copied to your computer.
- Check your current branch and repository status before pushing.
- Push rejections often mean the remote branch contains changes you need to integrate first.
- Git can merge changes automatically when they do not conflict.

## 8. Knowledge Check

1. What is the difference between `git push` and `git pull`?
2. What does it mean when your local branch is ahead of `origin/main` by one commit?
3. Why might Git reject a push?
4. What happens when you run `git pull`?
5. Why should you check `git status` before pushing?
