# GitHub: Resolving Conflicts

## 1. What Is a Merge Conflict?

A **merge conflict** occurs when Git cannot automatically combine changes from different branches, often because developers have modified the same lines of a file differently.

Git can automatically merge many changes. However, when it cannot determine which changes to keep, a developer must review and resolve the conflict manually.

**Common cause:** Two developers modify the same line of code on separate branches.

## 2. Example Scenario

Imagine two developers working on the same file, `Feature.js`.

- **Developer 1** works on `feature1`.
- **Developer 2** works on `feature2`.

Both developers create their branches from the same version of `main`. They then make different changes to the same line of code.

When Developer 1 merges their changes into `main`, Developer 2's branch becomes outdated. When Developer 2 attempts to integrate the latest changes from `main`, Git detects conflicting code.

## 3. Step 1 — Create Separate Branches

Both developers update their local `main` branch and create their own feature branches.

```bash
git switch main
git pull origin main
```

Developer 1:

```bash
git switch -c feature1
```

Developer 2:

```bash
git switch -c feature2
```

Each developer now has an independent branch for their work.

## 4. Step 2 — Developer 1 Merges Their Changes

Developer 1 modifies `Feature.js`, stages the file, and commits the changes.

```bash
git add Feature.js
git commit -m "Add feature 1"
git push -u origin feature1
```

Developer 1 then creates a pull request on GitHub. After the required reviews and checks, the pull request is merged into `main`.

The `main` branch now contains Developer 1's changes.

## 5. Step 3 — Developer 2 Encounters a Conflict

Developer 2 makes changes to the same file and commits them.

```bash
git add Feature.js
git commit -m "Add feature 2"
```

Before opening or updating their pull request, Developer 2 integrates the latest changes from `main`:

```bash
git pull origin main
```

If the changes cannot be combined automatically, Git reports a merge conflict.

Example output:

```text
Auto-merging Feature.js
CONFLICT (content): Merge conflict in Feature.js
Automatic merge failed; fix conflicts and then commit the result.
```

Git pauses the merge so the conflicting changes can be reviewed.

## 6. Step 4 — Identify the Conflict

Check the repository status:

```bash
git status
```

Git identifies files that require conflict resolution.

To inspect the conflicting changes, you can use:

```bash
git diff
```

In VS Code, open the file identified by Git. You will see conflict markers around the competing code.

Example:

```javascript
let add = (a, b) => {
<<<<<<< HEAD
  if (a + b > 10) { return 'way too much' }
=======
  if (a + b > 10) { return 'too much' }
>>>>>>> origin/main
  return a + b;
}
```

The two developers have written different messages for the same condition.

## 7. Step 5 — Understand Git Conflict Markers

Git uses special markers to separate the competing changes.

| Marker | Meaning |
|---|---|
| `<<<<<<< HEAD` | Begins the current branch's version of the conflicting section during a merge |
| `=======` | Separates the competing versions |
| `>>>>>>> origin/main` | Ends the incoming version from `origin/main` in this example |

The exact text after `>>>>>>>` may be a branch name or commit identifier.

**Important:** Conflict markers are temporary instructions for identifying the competing code. They must not remain in the final resolved file.

## 8. Step 6 — Resolve the Conflict in VS Code

VS Code provides buttons above conflicting sections, such as:

- **Accept Current Change** — keep the current branch's version.
- **Accept Incoming Change** — keep the incoming branch's version.
- **Accept Both Changes** — keep both versions for you to review.
- **Compare Changes** — inspect the differences.

The available buttons can vary depending on the editor and conflict type.

You can also resolve the conflict manually by editing the file.

For this example, Developer 2 decides to keep their wording. The resolved file becomes:

```javascript
let add = (a, b) => {
  if (a + b > 10) { return 'way too much' }
  return a + b;
}
```

The final file should contain the intended code without any conflict markers.

**Best practice:** Review the entire resolved section and ensure that the final code is logically correct. Do not simply choose one version without understanding the changes.

## 9. Step 7 — Stage and Commit the Resolution

Once the conflict has been resolved, stage the file:

```bash
git add Feature.js
```

Check the status:

```bash
git status
```

Complete the merge by creating a commit:

```bash
git commit -m "Resolve merge conflict in Feature.js"
```

Git records the merge resolution in the repository history.

## 10. Step 8 — Push the Updated Branch

Push Developer 2's branch to GitHub:

```bash
git push -u origin feature2
```

If upstream tracking has already been configured, the following is usually sufficient:

```bash
git push
```

Developer 2 can now create or update their pull request. The pull request can then be reviewed and merged when the required checks and approvals are satisfied.

## 11. Complete Conflict Resolution Workflow

```text
1. Create separate feature branches
              ↓
2. Developer 1 merges changes into main
              ↓
3. Developer 2 integrates the latest main
              ↓
4. Git detects conflicting changes
              ↓
5. Inspect the conflicting file
              ↓
6. Resolve the conflict in VS Code
              ↓
7. Stage the resolved file
              ↓
8. Commit the merge resolution
              ↓
9. Push the updated feature branch
              ↓
10. Update and complete the pull request
```

## 12. Key Takeaways

- A merge conflict occurs when Git cannot automatically combine changes.
- Conflicts commonly happen when developers edit the same lines differently.
- `git status` identifies files that need attention.
- `git diff` helps inspect conflicting changes.
- Conflict markers show the competing versions of the code.
- VS Code can help resolve conflicts using its built-in merge controls.
- Remove all conflict markers before completing the resolution.
- Review and test the final code before committing.
- `git add` stages the resolved file.
- `git commit` records the resolution.
- `git push` uploads the updated branch to GitHub.
- Merge conflicts are a normal part of collaborative software development.

## Commands to Remember

| Command | Purpose |

| `git status` | Check repository status and identify conflicts |
| `git diff` | Inspect changes |
| `git pull origin main` | Fetch and integrate changes from `main` |
| `git add Feature.js` | Stage the resolved file |
| `git commit -m "Resolve merge conflict"` | Commit the resolution |
| `git push` | Push the updated branch |

