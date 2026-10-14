# Change Directory and List Contents

## 1. Introduction

The Linux command line allows us to navigate the filesystem, inspect directories, and find files using terminal commands.

In this lesson, we learn how to:

- Display the current working directory.
- List files and directories.
- Understand file types and permissions.
- Navigate between directories.
- Use relative and absolute paths.

## 2. The `pwd` Command

`pwd` stands for **Print Working Directory**. It displays the full path of the directory you are currently in.

```bash
pwd
```

Example output:

```text
/
```

The forward slash `/` represents the **root directory**, which is the top-level directory of the Linux filesystem.

## 3. The `ls` Command

`ls` stands for **list**. It displays the contents of a directory.

```bash
ls
```

To display the contents in a detailed, long-list format:

```bash
ls -l
```

The `-l` flag displays additional information, including permissions, ownership, file size, and modification time.

To include hidden files and directories:

```bash
ls -la
```

Files and directories whose names begin with a dot (`.`) are typically hidden.

### What is a flag?

A **flag** is an option added to a command to change its behaviour.

Examples:

- `-l`: use long-list format.
- `-a`: include hidden files.
- `-la`: combine both options.

## 4. Understanding File Types

When you run `ls -l`, the first character indicates the file type.

| Symbol | Meaning |
|---|---|
| `-` | Regular file |
| `d` | Directory |
| `l` | Symbolic link |

Example:

```text
drwxr-xr-x  2 root root 4096 Oct 14 09:00 bin
-rw-r--r--  1 root root  120 Oct 14 09:00 resolv.conf
lrwxrwxrwx  1 root root    4 Oct 14 09:00 temp -> tmp
```

In this example:

- `bin` is a directory because its permissions begin with `d`.
- `resolv.conf` is a regular file because its permissions begin with `-`.
- `temp` is a symbolic link because its permissions begin with `l`. It points to `tmp`.

The owner and group columns identify the user and group associated with the file or directory.

## 5. The `cd` Command

`cd` stands for **Change Directory**. It allows you to move from one directory to another.

### Change into a directory

```bash
cd etc
```

This enters the `etc` directory if it exists inside your current directory and you have permission to access it.

List its contents:

```bash
ls
```

Confirm your location:

```bash
pwd
```

If you started in `/`, the resulting path will be `/etc`.

### Move to the parent directory

```bash
cd ..
```

The two dots (`..`) represent the parent directory.

For example:

```text
/etc/ssh
```

Running `cd ..` from `/etc/ssh` takes you to:

```text
/etc
```

Running `cd ..` again takes you to:

```text
/
```

### Move directly to the root directory

```bash
cd /
```

This moves directly to the root directory, regardless of your current location.

Verify it:

```bash
pwd
```

Expected output:

```text
/
```

### Navigate into nested directories

From the root directory, you can enter `etc`, then `ssh`:

```bash
cd /etc
cd ssh
ls
pwd
```

You can also navigate directly using the full path:

```bash
cd /etc/ssh
```

## 6. Absolute Paths vs Relative Paths

### Absolute path

An **absolute path** starts from the root directory (`/`) and identifies a location in the filesystem.

Example:

```bash
cd /etc/ssh
```

This specifies the complete path to the `ssh` directory.

### Relative path

A **relative path** is interpreted from your current working directory.

Example, when you are already in `/etc`:

```bash
cd ssh
```

This enters `/etc/ssh`.

### Comparison

| Command | Meaning |
|---|---|
| `cd /` | Go to the root directory |
| `cd /etc` | Go to `/etc` using an absolute path |
| `cd etc` | Enter `etc` inside the current directory |
| `cd ..` | Move to the parent directory |
| `cd /etc/ssh` | Go directly to `/etc/ssh` |
| `pwd` | Display the current directory |

## 7. Important Directory Concepts

- `/` — root directory; the top of the Linux filesystem.
- `.` — the current directory.
- `..` — the parent directory.
- `~` — the current user's home directory.

For example:

```bash
cd ~
```

This moves to your home directory.

**Remember:** The root directory `/` and the home directory `~` are not the same location.

## 8. Practical Example

Follow these commands in order on a Linux system:

```bash
pwd
ls
ls -l
cd /etc
pwd
ls
ls -l
cd ssh
pwd
ls
cd ..
pwd
cd ..
pwd
```

Observe how the output of `ls` changes as you move between directories.

Note: The `/etc/ssh` directory and its contents depend on the Linux system and your permissions.

## 9. Common Mistakes

| Mistake | Explanation or solution |
|---|---|
| Using `ls` when you want your location | Use `pwd` to display the current working directory. |
| Confusing `/` with `~` | `/` is the filesystem root; `~` is your home directory. |
| Running `cd ..` expecting to enter a child directory | `cd ..` moves up to the parent directory. |
| Using a relative path from the wrong directory | Run `pwd` first or use an absolute path. |
| Assuming `ls` shows hidden files | Use `ls -a` or `ls -la`. |
| Confusing a symbolic link with a regular directory | Check the first character in the output of `ls -l`. |

## 10. Key Takeaways

- `pwd` displays where you are.
- `ls` lists directory contents.
- `ls -l` provides detailed file information.
- `ls -la` also includes hidden files.
- `cd` changes directories.
- `cd ..` moves to the parent directory.
- `cd /` moves to the root directory.
- Absolute paths start from `/`; relative paths start from your current location.
- The first character in `ls -l` output indicates whether an entry is a regular file, directory, or symbolic link.

## 11. Practice Questions

1. What does `pwd` stand for?
2. What does the root directory `/` represent?
3. What is the difference between `ls` and `ls -l`?
4. How do you list hidden files?
5. What do `-`, `d`, and `l` mean in `ls -l` output?
6. What does `cd ..` do?
7. What is the difference between an absolute path and a relative path?
8. How do you navigate directly to `/etc/ssh`?
9. What is the difference between `/` and `~`?
10. Which command would you use to confirm that you are in `/etc`?

## 12. Practical Challenge

Complete the following tasks in your terminal without copying the commands from your notes:

1. Display your current working directory.
2. List its contents.
3. List its contents in long format.
4. Navigate to `/etc`.
5. Display the current directory again.
6. List the contents of `/etc`.
7. Navigate to `/etc/ssh`.
8. Move back to `/etc` using `cd ..`.
9. Return to the root directory using `cd /`.
10. Confirm your final location with `pwd`.
