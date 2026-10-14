# Creating and Running Bash Scripts

## 1. What Is Bash?

**Bash** stands for *Bourne Again Shell*. It is a command-line shell that allows users to interact with an operating system by entering commands.

Bash can also execute scripts containing multiple commands. These scripts are useful for automating repetitive tasks.

## 2. Navigating to the Home Directory

### Commands

```bash
cd ~
```

- `cd` means change directory.
- `~` represents the current user's home directory.

To list all files, including hidden files, in a detailed format:

```bash
ls -la
```

- `ls` lists files and directories.
- `-l` displays detailed information, including permissions.
- `-a` includes hidden files, which usually begin with a dot (`.`).

## 3. Understanding `.bashrc` and `.bash_profile`

These files are used to configure the Bash environment.

### `.bashrc`

The `.bashrc` file typically contains interactive shell configuration, such as:

- Shell aliases and functions.
- Command history settings.
- Prompt appearance and colours.
- Other settings used in interactive Bash sessions.

To view the file:

```bash
less ~/.bashrc
```

Press `q` to exit the `less` viewer.

### `.bash_profile`

The `.bash_profile` file is commonly used for login-shell configuration. It can set environment variables and run startup commands.

For example, environment variables can store paths or configuration values used by development tools.

To view the file:

```bash
less ~/.bash_profile
```

Press `q` to exit.

**Important:** Startup-file behaviour depends on the shell and operating system. On many Linux systems, `.bash_profile` is read by login shells, while `.bashrc` is read by interactive non-login shells. A login profile often loads `.bashrc` as well.

## 4. Creating a Bash Script

A Bash script is a text file containing commands that Bash can execute.

In the video, the script is named `testshell.sh`.

### Step 1: Open the editor

```bash
vim testshell.sh
```

This opens Vim and creates the file if it does not already exist.

### Step 2: Enter insert mode

Press `i` to enter insert mode so you can type into the file.

### Step 3: Write the script

```bash
#!/bin/bash

echo "Hello World"
```

### Understanding the code

- `#!/bin/bash` is called the **shebang**. It identifies the interpreter used to execute the script.
- `echo` prints text to the terminal.
- `"Hello World"` is the text being printed.

### Step 4: Save and exit Vim

1. Press `Esc` to leave insert mode.
2. Type `:wq`.
3. Press `Enter`.

In Vim:
- `:w` saves the file.
- `:q` quits the editor.
- `:wq` saves and quits.

## 5. Checking File Permissions

After saving the script, run:

```bash
ls -la
```

The script may not yet have execute permission. You can inspect its permissions in the output.

For example:

```text
-rw-r--r--  1 user user  34 Oct 14 09:00 testshell.sh
```

The first character and following permission characters indicate the file type and access permissions.

## 6. Making the Script Executable

Use the `chmod` command:

```bash
chmod 755 testshell.sh
```

`chmod` changes file permissions.

The numeric permission values are:

| Number | Permission |
|---|---|
| `4` | Read |
| `2` | Write |
| `1` | Execute |
| `7` | Read, write and execute (`4 + 2 + 1`) |
| `5` | Read and execute (`4 + 1`) |

Therefore, `755` means:

- **Owner:** read, write and execute (`7`).
- **Group:** read and execute (`5`).
- **Others:** read and execute (`5`).

Verify the change:

```bash
ls -la
```

The permissions should now look similar to:

```text
-rwxr-xr-x  1 user user  34 Oct 14 09:00 testshell.sh
```

The `x` characters indicate that execute permission has been granted.

## 7. Running the Bash Script

Run the script from the current directory:

```bash
./testshell.sh
```

### Why use `./`?

- `.` represents the current directory.
- `/` separates the directory from the filename.
- `./testshell.sh` tells the shell to execute the script located in the current directory.

Expected output:

```text
Hello World
```

An alternative is to execute the script explicitly through Bash:

```bash
bash testshell.sh
```

This alternative normally does not require the file to have execute permission because Bash reads the script directly.

## 8. Complete Command Sequence

Use these commands to reproduce the exercise:

```bash
cd ~
ls -la
less ~/.bashrc
less ~/.bash_profile
vim testshell.sh
chmod 755 testshell.sh
ls -la
./testshell.sh
```

Remember to press `q` after viewing each file with `less`, and save the script in Vim before running it.

## 9. Common Errors

| Error | Possible solution |
|---|---|
| `Permission denied` | Check execute permissions with `ls -l`, then use `chmod 755 testshell.sh` if appropriate. |
| `No such file or directory` | Check the filename and current directory with `pwd` and `ls`. |
| `vim: command not found` | Use an installed text editor, such as `nano`, or install Vim if permitted. |
| `bad interpreter` | Check the shebang and whether the script has Windows-style line endings. |
| `command not found` when running the script | Use `./testshell.sh` rather than just `testshell.sh`. |

## 10. Key Takeaways

- Bash is a shell and scripting language.
- `cd ~` navigates to the home directory.
- `ls -la` lists files, including hidden files, with detailed information.
- `.bashrc` commonly configures interactive shells.
- `.bash_profile` commonly configures login shells.
- A shebang specifies the script interpreter.
- `echo` prints text.
- `chmod 755` grants the owner full permissions and grants the group and others read and execute permissions.
- `./scriptname.sh` runs an executable script in the current directory.

## 11. Practice Questions

1. What does Bash stand for?
2. What is the difference between `ls` and `ls -la`?
3. What is the purpose of the shebang (`#!/bin/bash`)?
4. What does the `echo` command do?
5. What does `chmod` change?
6. What permissions does `755` represent?
7. Why do we use `./testshell.sh` to run the script?
8. What is the difference between running `./testshell.sh` and `bash testshell.sh`?
9. Which key exits the `less` viewer?
10. Which Vim command saves a file and exits?

## 12. Practical Challenge

Create a script named `developer.sh` that:

1. Prints `Welcome to my developer environment!`
2. Prints `I am learning Bash scripting.`
3. Prints the current working directory using `pwd`.

Make it executable and run it from your terminal.

**Hint:** Use `echo` for the messages and `pwd` to display the current directory.
