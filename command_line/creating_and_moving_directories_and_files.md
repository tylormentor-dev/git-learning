# Creating and Moving Directories and Files

## 1. Introduction

In Linux, the command line allows you to create directories, create files, move directories and files, and inspect their contents.

In this lesson, we learn how to use:

- `pwd` — display the current working directory.
- `ls -l` — list directory contents in long format.
- `mkdir` — create directories.
- `cd` — change directories.
- `touch` — create empty files.
- `mv` — move or rename files and directories.
- `clear` — clear the terminal screen.

## 2. Check the Current Directory

Use `pwd` to display your current working directory.

```bash
pwd
```

Example output:

```text
/
```

The forward slash `/` represents the root directory, which is the top-level directory in the Linux filesystem.

To list its contents in long format, use:

```bash
ls -l
```

## 3. Creating a Directory with `mkdir`

The `mkdir` command stands for **make directory**. It creates a new directory.

### Example

```bash
mkdir submissions
```

This creates a directory called `submissions` in your current working directory.

To verify that it was created, run:

```bash
ls -l
```

The new directory should appear in the output.

### Important points

- `mkdir` creates directories.
- The directory is created relative to your current location unless you specify a path.
- The directory name must not conflict with an existing file or directory of the same name in that location.

## 4. Moving into a Directory

Use `cd` to enter the new directory.

```bash
cd submissions
```

Check its contents:

```bash
ls
```

If the directory is empty, no filenames will be displayed.

To confirm your location, use:

```bash
pwd
```

## 5. Creating Files with `touch`

The `touch` command can create an empty file if that file does not already exist.

Inside the `submissions` directory, create two files:

```bash
touch test1.txt
touch test2.txt
```

You can also create both files in one command:

```bash
touch test1.txt test2.txt
```

List the files:

```bash
ls -l
```

You should now see `test1.txt` and `test2.txt`.

**Note:** If a file already exists, `touch` updates its timestamps rather than replacing its contents.

## 6. Returning to the Parent Directory

To move up one directory level, use:

```bash
cd ..
```

The two dots (`..`) represent the parent directory.

For example, if you are in `/submissions`, running `cd ..` takes you back to `/`.

Check your location and list the contents:

```bash
pwd
ls -l
```

## 7. Creating Another Directory

Create a directory called `archive`:

```bash
mkdir archive
```

List the contents:

```bash
ls -l
```

You should now see the directories `projects`, `submissions`, and `archive`, assuming `projects` was already present in the starting directory.

## 8. Clearing the Terminal Screen

Use the `clear` command to clear the visible terminal screen.

```bash
clear
```

This clears the display; it does not delete files, directories, or command history.

After clearing the screen, run:

```bash
ls -l
```

The directory contents will be displayed again.

## 9. Moving Directories with `mv`

The `mv` command moves or renames files and directories.

### Move a directory into another directory

To move `submissions` into `archive`, run this command from the parent directory containing both:

```bash
mv submissions archive
```

The directory structure becomes:

```text
/
├── projects/
└── archive/
    └── submissions/
        ├── test1.txt
        └── test2.txt
```

This is an illustrative structure based on the example in the lesson.

### Verify the move

List the current directory:

```bash
ls -l
```

The `submissions` directory should no longer appear directly in the current directory because it has been moved into `archive`.

Enter `archive`:

```bash
cd archive
```

List its contents:

```bash
ls -l
```

You should see `submissions`.

Enter the moved directory:

```bash
cd submissions
```

List the files:

```bash
ls -l
```

The files `test1.txt` and `test2.txt` should still be there. Moving a directory also moves its contents.

## 10. Moving Files with `mv`

The same command can move individual files.

For example, to move `test1.txt` into an existing directory called `archive`, run this from the directory containing `test1.txt`:

```bash
mv test1.txt archive/
```

The general syntax is:

```bash
mv SOURCE DESTINATION
```

- `SOURCE` is the file or directory you want to move.
- `DESTINATION` is the target directory or path.

### Renaming a file

You can also use `mv` to rename a file:

```bash
mv test1.txt first_test.txt
```

If `first_test.txt` does not exist, the file is renamed to `first_test.txt`.

**Caution:** `mv` can overwrite an existing destination file. Check the destination before moving or renaming important files.

## 11. Command Summary

| Command | Purpose |
|---|---|
| `pwd` | Displays the current working directory |
| `ls -l` | Lists contents in long format |
| `mkdir submissions` | Creates a directory named `submissions` |
| `cd submissions` | Enters the `submissions` directory |
| `touch test1.txt` | Creates an empty file if it does not exist |
| `cd ..` | Moves to the parent directory |
| `mkdir archive` | Creates a directory named `archive` |
| `clear` | Clears the terminal display |
| `mv submissions archive` | Moves `submissions` into `archive` |
| `mv old.txt new.txt` | Renames a file when the destination does not exist |

## 12. Complete Practice Exercise

Run these commands in order in a test directory where you have permission to create files and folders.

```bash
pwd
mkdir submissions
cd submissions
touch test1.txt test2.txt
ls -l
cd ..
mkdir archive
ls -l
mv submissions archive
ls -l
cd archive
ls -l
cd submissions
ls -l
```

Expected final result: the `archive` directory contains `submissions`, and `submissions` contains `test1.txt` and `test2.txt`.

If you already have a directory called `submissions` or `archive`, choose different names or use a separate practice directory to avoid conflicts.

## 13. Practice Questions

1. What does `mkdir` stand for?
2. What is the purpose of the `touch` command?
3. What does `cd ..` do?
4. How can you verify that a directory was created?
5. What is the purpose of `clear`?
6. What does `mv submissions archive` do when both directories are in the current directory?
7. What happens to files inside a directory when that directory is moved?
8. How can you rename `test1.txt` to `first_test.txt`?
9. What is the difference between `mkdir` and `touch`?
10. Why should you check a destination before using `mv`?

## 14. Key Takeaways

- Use `mkdir` to create directories.
- Use `touch` to create empty files.
- Use `cd` to navigate through directories.
- Use `cd ..` to move to a parent directory.
- Use `ls -l` to inspect directory contents.
- Use `mv` to move or rename files and directories.
- Use `clear` to clear the visible terminal screen.
- Verify your commands using `pwd` and `ls`.
