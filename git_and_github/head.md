# GitHub: HEAD

## 1. What Is HEAD?

In Git, **`HEAD` is a pointer that identifies your current position in the repository**, usually the branch you are currently working on.

Git stores repository information inside a hidden directory called `.git`.

`HEAD` helps Git determine which branch you are working on and where new commits should be made.

For example, when you are working on the `main` branch, `HEAD` normally points to that branch.

## 2. Where Is HEAD Stored?

The `HEAD` file is located inside the `.git` directory.

To view its contents, run:

```bash
cat .git/HEAD
```

Example output:

```text
ref: refs/heads/main
```

This means that `HEAD` points to the local `main` branch.

The path `refs/heads/main` identifies the reference for the `main` branch.

## 3. How HEAD Points to a Branch

Git normally works on one checked-out branch at a time.

For example, a repository may contain these branches:

- `main`
- `testing`
- `feature/testing-branches`

When you switch branches, `HEAD` normally updates to point to the newly selected branch.

To view your current branch:

```bash
git branch
```

The current branch is marked with an asterisk (`*`).

To switch branches:

```bash
git switch testing
```

Check the `HEAD` file again:

```bash
cat .git/HEAD
```

Example output:

```text
ref: refs/heads/testing
```

`HEAD` now points to the `testing` branch instead of `main`.

You can switch back using:

```bash
git switch main
```

## 4. How Branch References Work

Inside `.git`, the `refs/heads/` directory contains references to local branches.

For example:

```text
.git/
├── HEAD
└── refs/
    └── heads/
        ├── main
        └── testing
```

The `main` and `testing` files contain references to the latest commits on their respective branches.

To inspect the local `main` branch reference, run:

```bash
cat .git/refs/heads/main
```

Example output:

```text
8b55a1c...
```

This is an abbreviated example of a commit hash. The actual output is a full object ID, usually 40 hexadecimal characters in a SHA-1 repository.

**Important:** These internal files are implementation details. Commands such as `git branch`, `git log`, and `git rev-parse` are generally more reliable for everyday Git work.

## 5. What Happens When You Modify a File?

Suppose you edit `README.md`.

Before committing, check the repository status:

```bash
git status
```

Git may show:

```text
modified: README.md
```

The file has changed, but you have not created a new commit yet.

**The current branch's commit reference does not change just because you edit or stage a file.** It changes when a new commit is created on that branch.

## 6. Create a Commit and Observe HEAD

Follow these steps to see how a commit affects the branch reference.

### Step 1 — Check the Current Commit

```bash
git log -1 --oneline
```

This displays the latest commit on the current branch.

You can also inspect the current commit ID directly:

```bash
git rev-parse HEAD
```

### Step 2 — Edit a File

Open `README.md` in VS Code and make a small change.

Check the status:

```bash
git status
```

### Step 3 — Stage the Change

```bash
git add README.md
```

### Step 4 — Commit the Change

```bash
git commit -m "Update README"
```

### Step 5 — Check HEAD Again

```bash
git rev-parse HEAD
```

The commit ID should now be different from the previous one because you created a new commit.

The local branch reference, such as `main`, now points to the new commit, and `HEAD` points to that branch.

## 7. HEAD and Branches

The relationship between `HEAD`, branches, and commits can be represented as follows:

```text
HEAD
 |
 v
main branch
 |
 v
Latest commit
 |
 v
Previous commit
```

When you create a new commit on `main`, the `main` branch reference advances to the new commit. `HEAD` continues pointing to `main`.

When you switch to another branch, `HEAD` points to that branch instead.

## 8. Attached HEAD vs Detached HEAD

### Attached HEAD

This is the normal state when you are working on a branch.

Example:

```text
HEAD -> main -> commit
```

New commits advance the current branch reference.

### Detached HEAD

A detached `HEAD` occurs when you check out a commit directly instead of checking out a branch.

For example:

```bash
git switch --detach <commit-hash>
```

In this state, `HEAD` points directly to a commit rather than to a branch reference.

You can inspect old commits in this state, but if you create new commits, they may not belong to a named branch. Create a branch if you want to keep that work safely.

## 9. Key Takeaways

- `HEAD` identifies your current position in the repository.
- The `.git/HEAD` file normally contains a reference to your current local branch.
- `git switch` changes the branch that `HEAD` points to.
- Files inside `.git/refs/heads/` store local branch references in a traditional repository layout.
- Editing or staging files does not change the latest commit reference.
- Creating a commit advances the current branch reference.
- A detached `HEAD` points directly to a commit instead of a branch.
- Use Git commands rather than manually editing files inside `.git`.

## Commands to Remember

| Command | Purpose |
|---|---|
| `git status` | Check changes in the working tree |
| `git branch` | List local branches |
| `git switch main` | Switch to the `main` branch |
| `cat .git/HEAD` | Inspect the HEAD file |
| `git rev-parse HEAD` | Display the current commit ID |
| `git log -1 --oneline` | Display the latest commit |
| `git add README.md` | Stage a file |
| `git commit -m "Update README"` | Create a commit |
| `git switch --detach <commit-hash>` | Check out a commit directly |

