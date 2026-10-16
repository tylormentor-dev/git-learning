# Diff Commands

## 1. What Is `git diff`?

`git diff` is a Git command used to compare changes in files, commits, and branches. It shows you **exactly what has been added, removed, or changed**.

- `git status` tells you which files have changed.
- `git diff` shows you the actual differences in their contents.

## 2. Understanding the Diff Output

When you run `git diff`, Git displays the changes between two versions of your work.

| Symbol | Meaning |
|---|---|
| `-` | A line that was removed or replaced |
| `+` | A line that was added or replaced |

For example:

```diff
- This is the original sentence.
+ This is the updated sentence.
```

The minus sign represents the original line, while the plus sign represents the new line.

## 3. Comparing Working-Directory Changes

Use `git diff` to compare your modified files against the staged version or the last committed version, depending on the command.

### View unstaged changes

```bash
git diff
```

Shows changes you have made but have **not yet staged** with `git add`.

### Compare a specific file

```bash
git diff -- README.md
```

Shows unstaged changes in `README.md`.

### Compare against `HEAD`

```bash
git diff HEAD -- README.md
```

Shows all changes in `README.md` since the latest commit, including both staged and unstaged changes.

## 4. Comparing Commits

You can compare two commits to see how your project changed between them.

### View commit history

```bash
git log --oneline
```

Displays the commit history in a compact format, including each commit's ID and message.

### Compare two commits

```bash
git diff <older-commit> <newer-commit>
```

Replace the placeholders with the actual commit IDs.

Git displays the differences between the two commits across the files that changed.

## 5. Comparing Branches

You can use `git diff` to compare the changes in two branches without switching between them.

### List available branches

```bash
git branch
```

### Compare two branches

```bash
git diff main feature-branch
```

This shows the differences between the tips of `main` and `feature-branch`.

The order matters: Git presents the changes needed to transform the first comparison target into the second.

To compare the common ancestor of the branches with the feature branch (often useful for reviewing feature work), use:

```bash
git diff main...feature-branch
```

This shows changes introduced on `feature-branch` since it diverged from `main`.

## 6. Quick Reference

| Command | Purpose |
|---|---|
| `git status` | Shows which files have changed |
| `git diff` | Shows unstaged changes |
| `git diff -- README.md` | Shows unstaged changes in a specific file |
| `git diff HEAD` | Shows staged and unstaged changes since the last commit |
| `git log --oneline` | Shows a compact commit history |
| `git diff <commit1> <commit2>` | Compares two commits |
| `git branch` | Lists local branches |
| `git diff main feature-branch` | Compares two branch tips |
| `git diff main...feature-branch` | Shows feature-branch changes since divergence from `main` |

## 7. Key Takeaways

- Use `git status` to identify which files have changed.
- Use `git diff` to inspect the actual changes before committing.
- A minus sign (`-`) marks removed lines, and a plus sign (`+`) marks added lines.
- You can compare working-directory changes, commits, and branches.
- Reviewing diffs helps you catch mistakes and understand changes before merging or committing.
