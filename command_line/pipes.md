# Pipes

## 1. What Are Pipes?

A **pipe (`|`)** is a command-line operator that passes the output of one command as the input to another command.

Pipes allow us to combine commands to perform tasks more efficiently without saving intermediate results to a file.

### Syntax

```bash
command1 | command2
```

- `command1`: Produces output.
- `|`: Passes the output to the next command.
- `command2`: Processes the received input.

**Example:**

```bash
cat file1.txt | wc -w
```

This command displays the contents of `file1.txt` and passes the text to `wc -w`, which counts the words.

---

## 2. Essential Terminal Commands

| Command | Description | Example |
|---|---|---|
| `pwd` | Displays the current working directory. | `pwd` |
| `ls` | Lists files and directories. | `ls` |
| `cd` | Changes the current directory. | `cd archive` |
| `cat` | Displays or combines file contents. | `cat file1.txt` |
| `wc` | Counts lines, words, and bytes. | `wc -w file1.txt` |
| `\|` | Passes output from one command to another. | `cat file1.txt \| wc -w` |

---

## 3. Navigating Directories

Suppose the current directory contains two folders: `archive` and `projects`.

```bash
ls
```

Navigate into `archive`:

```bash
cd archive
ls
```

Navigate into `submissions`:

```bash
cd submissions
ls
```

The directory structure might look like this:

```text
archive/
└── submissions/
    ├── file1.txt
    └── file2.txt
```

Use `pwd` to check your current location:

```bash
pwd
```

---

## 4. Reading File Contents

The `cat` command displays the contents of a file.

```bash
cat file1.txt
```

To display the contents of two files consecutively:

```bash
cat file1.txt file2.txt
```

This is useful when you want to inspect files or combine their contents for further processing.

---

## 5. Counting Words with `wc`

The `wc` command stands for **word count**. It can count lines, words, and bytes.

### Count words in one file

```bash
wc -w file1.txt
```

Example output:

```text
181 file1.txt
```

The `-w` option counts words. In this example, `file1.txt` contains 181 words.

### Other useful `wc` options

| Option | Description | Example |
|---|---|---|
| `-w` | Counts words. | `wc -w file1.txt` |
| `-l` | Counts lines. | `wc -l file1.txt` |
| `-c` | Counts bytes. | `wc -c file1.txt` |

---

## 6. Using Pipes to Count Words

### Example 1: Count words in one file

```bash
cat file1.txt | wc -w
```

**How it works:**

1. `cat file1.txt` outputs the file's contents.
2. `|` passes the output to the next command.
3. `wc -w` counts the words it receives.

Expected result:

```text
181
```

You can also run `wc -w file1.txt` directly. The pipe demonstrates how commands can be connected.

### Example 2: Process the output of `ls`

```bash
ls | wc -w
```

This counts the whitespace-separated words in the output of `ls`.

If `ls` displays two filenames, the result may be `2`.

**Important:** This is not a reliable general-purpose file-counting method because filenames and formatting can affect the result.

### Example 3: Count words across two files

```bash
cat file1.txt file2.txt | wc -w
```

This combines the contents of both files and passes them to `wc -w`.

If each file contains 181 words, the total is:

```text
362
```

The total word count is calculated by adding the words in both files.

---

## 7. Important Concepts

### Standard output

**Standard output (`stdout`)** is the normal output produced by a command.

For example:

```bash
ls
```

The filenames are written to standard output.

### Standard input

**Standard input (`stdin`)** is the input a command reads for processing.

A pipe connects the standard output of one command to the standard input of another.

For example:

```bash
cat file1.txt | wc -w
```

The text produced by `cat` becomes the input processed by `wc`.

### Command chaining

Command chaining allows multiple commands to work together.

```bash
command1 | command2 | command3
```

Each pipe passes the previous command's output to the next command.

---

## 8. Common Mistakes

- **Confusing `|` with `>`:** A pipe passes output to another command, while `>` redirects output to a file.
- **Using the wrong directory:** Check your location with `pwd` before running commands.
- **Forgetting filenames:** Ensure the file exists in the current directory or provide its correct path.
- **Assuming `ls | wc -w` always counts files:** It counts words in the command output, not files directly.
- **Using unnecessary pipes:** If a command can perform the task directly, prefer the simpler command when appropriate.

---

## 9. Quick Reference

```bash
# List files and directories
ls

# Navigate into a directory
cd archive

# Display the current directory
pwd

# Display a file's contents
cat file1.txt

# Count words in a file
wc -w file1.txt

# Count lines in a file
wc -l file1.txt

# Count words using a pipe
cat file1.txt | wc -w

# Count combined words in two files
cat file1.txt file2.txt | wc -w

# Pass the output of one command to another
command1 | command2
```

---

## 10. Key Takeaways

- A pipe (`|`) connects commands by passing output from one command to another.
- `cat` displays file contents and can combine the contents of multiple files.
- `wc -w` counts words, `wc -l` counts lines, and `wc -c` counts bytes.
- Pipes can be chained to create more complex command-line workflows.
- Understanding pipes is useful for Linux, Git, software development, automation, and CI/CD workflows.

## 11. Practice Exercises

Try these exercises in your terminal:

1. List the files and directories in your current directory.
2. Navigate into a directory and display its contents.
3. Display the contents of `file1.txt`.
4. Count the words in `file1.txt` using `wc`.
5. Count the words in `file1.txt` using a pipe.
6. Count the combined words in `file1.txt` and `file2.txt`.
7. Count the lines in `file1.txt` using `wc -l`.
8. Explain the difference between `|` and `>` in your own words.