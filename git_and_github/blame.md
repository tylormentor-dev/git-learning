# Git Blame

## 1. What Is `git blame`?

`git blame` is a Git command used to identify **who last modified each line of a file and when the change was made**.

Git tracks the history of changes made to files in a repository. The `git blame` command helps developers investigate this history, making it easier to understand how a file has changed over time.

### Why Use `git blame`?

- Identify who last changed a particular line of code.
- Find the commit associated with a change.
- View when a line was last modified.
- Understand the history of a file.
- Investigate bugs and understand previous code changes.

## 2. Basic Syntax

```bash
git blame <filename>
```

**Example:**

```bash
git blame feature.js
```

This displays information about the lines in `feature.js`, including the commit, author, timestamp, line number, and line content.

You must specify the file you want to investigate.

## 3. Understanding the Output

Each line of `git blame` output contains information about the history of that line.

The output generally includes:

| Field | Description |
|---|---|
| Commit hash | Identifies the commit associated with the line's current content. |
| Author | The person credited with the change. |
| Timestamp | The date and time associated with the change. |
| Line number | The line's current position in the file. |
| Code content | The actual content of the line. |

**Important:** The same commit hash can appear on multiple lines because one commit can introduce or modify several lines.

Also, `git blame` identifies the commit associated with the current version of a line. It does not necessarily identify every developer who has ever worked on that line.

## 4. Viewing a Specific Range of Lines

When working with large files, viewing every line can make the output difficult to read.

You can use the `-L` option to display a specific range of lines.

### Syntax

```bash
git blame -L <start>,<end> <filename>
```

### Example

```bash
git blame -L 5,15 setup.py
```

This displays blame information for lines **5 through 15** of `setup.py`.

Use this option when investigating a particular section of a file.

## 5. Displaying Full Commit Hashes

Git normally displays abbreviated commit hashes. To display the full-length object IDs, use the `-l` option.

```bash
git blame -l setup.py
```

This makes it easier to copy the complete commit hash when investigating a specific change.

**Note:** The `-l` option displays the full object name; it does not select a line range.

## 6. Investigating a Commit in More Detail

`git blame` helps you identify which commit is associated with a line. You can then investigate that commit to understand the actual changes it introduced.

### Step 1: Find the Commit Hash

Run:

```bash
git blame setup.py
```

Identify and copy the commit hash associated with the line you want to investigate.

### Step 2: View the Commit's Changes

Use `git show` to inspect the commit:

```bash
git show <commit-hash>
```

Alternatively, use `git log -p` to view commit details and patches:

```bash
git log -p -1 <commit-hash>
```

The `-p` option displays the patch, while `-1` limits the output to one commit.

### Difference Between `git blame` and `git log`

| Command | Purpose |
|---|---|
| `git blame <filename>` | Shows the commit associated with each line in a file. |
| `git log` | Displays the repository's commit history. |
| `git show <commit-hash>` | Displays details and changes from a specific commit. |
| `git log -p` | Displays commit history together with patches showing changes. |

These commands work well together when investigating bugs or understanding why code was changed.

## 7. Useful Git Blame Commands

| Command | Purpose |
|---|---|
| `git blame feature.js` | Inspect the history associated with lines in `feature.js`. |
| `git blame setup.py` | Inspect the history associated with lines in `setup.py`. |
| `git blame -L 5,15 setup.py` | Inspect lines 5–15 of `setup.py`. |
| `git blame -l setup.py` | Display full commit object IDs. |
| `git show <commit-hash>` | Inspect a specific commit and its changes. |
| `git log -p -1 <commit-hash>` | View the patch for a specific commit. |

## 8. Key Takeaways

- `git blame` helps you investigate the history of individual lines in a file.
- It shows the associated commit, author, timestamp, line number, and content.
- Use `-L` to restrict the output to a specific range of lines.
- Use `-l` to display full commit hashes.
- Use `git show` or `git log -p` to investigate the actual changes introduced by a commit.
- `git blame` is particularly useful for debugging, code reviews, and understanding unfamiliar codebases.

## 9. Practice Exercise

Try these commands in a Git repository:

1. Choose a file that has been committed to Git.
2. Run `git blame <filename>`.
3. Identify the commit hash associated with one line.
4. Run `git blame -L 1,10 <filename>` to inspect the first ten lines.
5. Use `git show <commit-hash>` to investigate the associated commit.

**Goal:** Learn how to identify who last changed a line and investigate the commit responsible for that version of the code.