# Grep

## 1. What Is Grep?

`grep` stands for **Global Regular Expression Print**. It is a command-line utility used to search text for patterns and display matching lines.

You can use `grep` to:
- Search for words or patterns inside files.
- Find text that matches a particular search.
- Ignore case sensitivity.
- Match whole words instead of partial matches.
- Filter the output of another command using a pipe (`|`).

## 2. Basic Grep Syntax

```bash
grep "pattern" filename
```

- `grep` — the search command.
- `"pattern"` — the text or pattern you want to find.
- `filename` — the file you want to search.

### Example

Suppose `names.txt` contains:

```text
Sam
Samuel
Samantha
Alex
Adam
Mary
```

To search for names containing `Sam`, run:

```bash
grep "Sam" names.txt
```

Possible output:

```text
Sam
Samuel
Samantha
```

By default, `grep` is case-sensitive. Searching for `sam` is different from searching for `Sam`.

```bash
grep "sam" names.txt
```

This matches lowercase `sam`, not uppercase `Sam`, unless the text contains both forms.

**Important:** `grep` searches for a matching pattern anywhere in a line by default. It does not automatically search only at the beginning of a name.

## 3. Useful Grep Flags

A flag is an option that changes how a command behaves.

### `-i` — Ignore Case

Search without distinguishing between uppercase and lowercase letters.

```bash
grep -i "sam" names.txt
```

This can match `Sam`, `SAM`, `sam`, and other combinations of those letters.

### `-w` — Match Whole Words

Match a whole word rather than a word that appears as part of a larger word.

```bash
grep -w "Sam" names.txt
```

This matches `Sam` as a whole word, but not `Samuel` or `Samantha`.

**Note:** `-w` matches whole words, not necessarily entire lines. To match a line containing only `Sam`, use `-x`.

### `-x` — Match Entire Lines

```bash
grep -x "Sam" names.txt
```

This matches only a line whose entire contents are `Sam`.

### `-n` — Show Line Numbers

```bash
grep -n "Sam" names.txt
```

Displays matching lines with their line numbers.

### `-v` — Invert the Match

```bash
grep -v "Sam" names.txt
```

Displays lines that do **not** match `Sam`.

### `-r` — Search Recursively

```bash
grep -r "Sam" my_folder/
```

Searches files within a directory and its subdirectories.

### `-E` — Extended Regular Expressions

```bash
grep -E "Sam|Alex" names.txt
```

Matches lines containing either `Sam` or `Alex`.

The `|` inside the quoted pattern means **OR** in extended regular expressions. This differs from the shell pipe, which connects commands.

## 4. Search for Text at the Beginning or End of a Line

Regular expressions allow more precise searches.

### `^` — Beginning of a Line

```bash
grep "^Sam" names.txt
```

Matches lines that begin with `Sam`.

### `$` — End of a Line

```bash
grep "Sam$" names.txt
```

Matches lines that end with `Sam`.

These symbols are useful when you need to find a pattern in a specific position.

## 5. Combining Grep with Pipes

A pipe (`|`) passes the output of one command to another command as input.

### Example: Filter a Directory Listing

```bash
ls /bin
```

This displays entries in `/bin`.

To display only entries whose names contain `zip`:

```bash
ls /bin | grep "zip"
```

To ignore case:

```bash
ls /bin | grep -i "zip"
```

To match the whole word:

```bash
ls /bin | grep -w "zip"
```

The pipe sends the output of `ls /bin` to `grep`, which filters the results.

**Note:** This searches the names in the directory listing. It does not, by itself, verify that each matching file is executable.

## 6. Searching Across Multiple Files

You can search more than one file in a single command.

```bash
grep "error" app.log system.log
```

This searches both files for lines containing `error`.

To search every file in a directory and its subdirectories:

```bash
grep -r "error" logs/
```

To include line numbers in a recursive search:

```bash
grep -rn "error" logs/
```

## 7. Quick Reference

| Command | Purpose |
|---|---|
| `grep "Sam" names.txt` | Search for `Sam` |
| `grep -i "sam" names.txt` | Ignore case |
| `grep -w "Sam" names.txt` | Match a whole word |
| `grep -x "Sam" names.txt` | Match an entire line |
| `grep -n "Sam" names.txt` | Show line numbers |
| `grep -v "Sam" names.txt` | Show non-matching lines |
| `grep -r "Sam" folder/` | Search recursively |
| `grep "^Sam" names.txt` | Match at the beginning of a line |
| `grep "Sam$" names.txt` | Match at the end of a line |
| `ls /bin \| grep "zip"` | Filter command output |

## 8. Common Mistakes

1. **Forgetting case sensitivity:** `grep "sam"` does not normally match `Sam`. Use `-i` when case does not matter.
2. **Confusing whole-word and whole-line matches:** `-w` matches whole words; `-x` matches entire lines.
3. **Forgetting the filename:** `grep "pattern" filename` searches the specified file.
4. **Confusing the two meanings of `|`:** The shell pipe connects commands, while `|` inside a regular expression can represent OR when using `grep -E`.
5. **Expecting every search to find a result:** If no lines match, `grep` normally displays nothing and returns exit status `1`. This does not necessarily mean the command failed.

## 9. Practice Exercises

Use your own `names.txt` file to complete these exercises.

- [ ] Search for all names containing `Alex`.
- [ ] Search for `alex` without case sensitivity.
- [ ] Find names that begin with `Sam`.
- [ ] Find lines that contain the whole word `Sam`.
- [ ] Find lines that contain only `Sam`.
- [ ] Display matching names with line numbers.
- [ ] Display every line that does not contain `Sam`.
- [ ] Use a pipe to filter the output of `ls`.
- [ ] Search recursively for a word inside a directory.

## 10. Key Takeaways

- `grep` searches text using patterns.
- Searches are case-sensitive by default.
- Flags such as `-i`, `-w`, `-x`, `-n`, and `-v` change search behaviour.
- Regular expressions provide more precise matching.
- Pipes let you combine `grep` with other command-line utilities.
- `grep` is useful for searching logs, source code, configuration files, and large collections of text.
