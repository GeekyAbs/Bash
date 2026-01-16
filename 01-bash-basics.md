# Bash Basics — Section 1

This document contains notes from Section 1 of the Bash course. It covers essential commands and concepts used for basic shell navigation, file manipulation, and text processing. Each topic includes a short explanation and examples.

---

## 1. echo
Prints text or variables to the terminal.

### Examples
```bash
echo "Hello, World"
echo $HOME
```

---

## 2. touch
Creates a new empty file or updates the timestamp of an existing file.

### Examples
```bash
touch file.txt
touch a.txt b.txt c.txt
```

---

## 3. rm
Removes (deletes) files or directories.

### Examples
```bash
rm file.txt
rm -r directory_name
```

Note: Deleted files are not easily recoverable.

---

## 4. mv (move / rename)
Moves files between directories or renames files.

### Examples
```bash
mv me.txt you.txt
mv file.txt /path/to/directory/
```

---

## 5. history
Displays previously executed commands in the shell.

### Examples
```bash
history
!10
```

---

## 6. Hidden files (.)
Files starting with a dot (.) are hidden by default.

### Examples
```bash
touch .file.txt
ls -a
```

---

## 7. . (current directory)
Represents the current working directory.

### Examples
```bash
./script.sh
ls .
```

---

## 8. .. (parent directory)
Represents the parent directory (one level up).

### Examples
```bash
cd ..
cd ../..
```

---

## 9. cd -
Returns to the previous directory.

### Example
```bash
cd /var/log
cd -
```

---

## 10. cat
Displays the contents of a file.

### Examples
```bash
cat filename.txt
cat file1.txt file2.txt
```

---

## 11. grep
Searches for a word or pattern in a file.

### Example
```bash
grep error /var/log/syslog
```

---

## 12. grep with quoted patterns and anchors
Using quotes prevents special character interpretation.

Special characters:
- `^` matches the beginning of a line  
- `$` matches the end of a line  

### Examples
```bash
grep '^root' /etc/passwd
grep 'bash$' /etc/passwd
```

---

## 13. echo with redirection
Writes text into a file using redirection.

### Examples
```bash
echo "Hello Bash" > file.txt
echo "Another line" >> file.txt
```

---

## 14. grep -i
Performs a case-insensitive search.

### Example
```bash
grep -i error log.txt
```

---

## 15. grep -o
Displays only the matched portion of the line.

### Example
```bash
grep -o '^d.' filename.txt
```

---

## 16. less
A pager used to view large files one page at a time.

### Example
```bash
less filename.txt
```

Navigation:
- Space: next page
- b: previous page
- /word: search
- q: quit

---

## 17. type -a
Shows how a command is interpreted by the shell.

### Example
```bash
type -a ls
```

---

## 18. compgen -b
Lists all Bash built-in commands.

### Example
```bash
compgen -b
```

---

## Summary
This section introduced core Bash commands and concepts including:
- File creation, deletion, and movement
- Directory navigation
- Viewing and searching file contents
- Understanding shell behavior

These fundamentals are the foundation for scripting and advanced shell usage.
