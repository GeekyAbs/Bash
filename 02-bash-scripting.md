
This section builds on Bash basics and introduces scripting concepts such as file permissions, variables, loops, conditionals, user input, arguments, functions, and control flow. Each command or concept is explained for beginners, with examples and explanations of new syntax.

---

## 1. `rm` (remove)
Used to delete files or directories.

### Example
```bash
rm file.txt
````

Deletes a directory and its contents:

```bash
rm -r my_directory
```

---

## 2. `rm *`

Deletes **all files in the current directory** (not directories by default).

### Example

```bash
rm *
```

⚠️ Dangerous command. It deletes everything matching `*` without confirmation (unless `-i` is used).

---

## 3. `chmod +x` (change mode)

Changes file permissions. `+x` makes a file executable.

### Example

```bash
chmod +x script.sh
```

Now the script can be run as:

```bash
./script.sh
```

---

## 4. `cp` (copy)

Copies files or directories.

### Syntax

```bash
cp source destination
```

### Examples

```bash
cp file.txt backup.txt
```

Copy a directory:

```bash
cp -r dir1 dir2
```

---

## 5. Variables and expansion

Variables store values. No spaces around `=`.

### Example

```bash
name="ahsdba"
echo "hello $name"
```

- `$name` expands the variable
    
- Expansion works inside **double quotes**, not single quotes
    

---

## 6. Vim: delete a line

In Vim:

- `dd` deletes the entire current line

---

## 7. `for` loop (basic)

Loops over a list of values.

### Example

```bash
#!/usr/bin/env bash

for thing in foo bar baz bat; do
    echo "thing is $thing"
done
```

Explanation:

- `thing` is the loop variable
    
- Each word (`foo`, `bar`, etc.) is assigned one at a time
    

---

## 8. `bash -n` (syntax check)

Checks a script for syntax errors **without running it**.

### Example

```bash
bash -n script.sh
```

No output means syntax is valid.

---

## 9. `$?` (exit status)

Shows the exit code of the last command.

### Example

```bash
echo $?
```

- `0` → success
    
- non-zero → error
    

---

## 10. User input

Input from the user is read using `read`.

---

## 11. `read -p`

Prompts the user and stores input in a variable.

### Example

```bash
#!/usr/bin/env bash

read -p 'Enter your name: ' name
echo "hello $name"
```

- `-p` displays a prompt
    
- Input is stored in `name`
    

---

## 12. Pipes (`|`)

Sends output of one command as input to another.

### Example

```bash
echo abesh | hello
```

Explanation:

- `echo abesh` outputs text
    
- `|` pipes it into the `hello` command (or script)
    

---

## 13. `yes` command

Outputs `y` repeatedly until stopped.

### Example

```bash
yes
```

Useful for automating prompts (be careful).

---

## 14. Conditional logic with arguments

Script checks if an argument was provided.

### Script

```bash
#!/usr/bin/env bash

if [[ -n $1 ]]; then
    name=$1
else
    read -p "Enter your name: " name
fi

echo "hello $name"
```

Explanation:

- `$1` → first argument
    
- `-n` → string is not empty
    
- Uses argument if provided, otherwise asks user
    

---

## 15. `$0`, `$1`, `$2`, ...

Special variables for script arguments.

- `$0` → script name
    
- `$1` → first argument
    
- `$2` → second argument
    
- `$@` → all arguments
    

### Example

```bash
./script.sh Alice Bob
```

- `$1` = Alice
    
- `$2` = Bob
    

---

## 16. Looping over all arguments (`"$@"`)

Iterates over each argument safely.

### Example

```bash
#!/usr/bin/env bash

for thing in "$@"; do
    echo "thing is $thing"
done
```

`"$@"` preserves spaces in arguments.

---

## 17. Script calling another script

One script can execute another.

### Example

```bash
#!/usr/bin/env bash

for name in "$@"; do
    ./hello "$name"
done
```

Explanation:

- Calls `hello` script for each argument
    
- `hello` must be executable
    

---

## 18. Functions

Reusable blocks of code.

### Example

```bash
#!/usr/bin/env bash

greet() {
    local name=$1
    echo "hello $name"
}

for name in "$@"; do
    greet "$name"
done
```

Explanation:

- `greet` is a function
    
- `local` limits variable scope
    
- `$1` inside function is the first argument passed to it
    

---

## 19. Appending output to a file

Use `>>` to append instead of overwrite.

### Example

```bash
greet "$name" >> output.txt
```

---

## 20. Variable expansion and quotes

- Double quotes (`" "`) → variables expand
    
- Single quotes (`' '`) → variables do not expand
    

### Example

```bash
name="Alex"

echo "$name"
echo '$name'
```

Output:

```text
Alex
$name
```

---

## 21. Conditionals and file tests

Comparison and file checks.

### Example

```bash
#!/usr/bin/env bash

a=2
b=1

if [[ $a != $b ]]; then
    echo "a and b are not same"
fi

if [[ -f file.txt ]]; then
    echo "does exist"
fi
```

Explanation:

- `!=` → not equal
    
- `-f` → file exists and is a regular file
    

---

## 22. Vim visual mode

- `Shift + v` → line visual mode
    
- Use arrow keys or `j/k` to select lines
    

---

## 23. `while` loop

Runs while a condition is true.

### Example

```bash
#!/usr/bin/env bash

while [[ -f file.txt ]]; do
    echo 'file.txt exists and is a file'
    sleep 1
done

echo "file is gone"
```

Explanation:

- Loop runs as long as `file.txt` exists
    
- `sleep 1` pauses for 1 second
    

---

## 24. `until` vs `while`

- `while` → runs **while condition is true**
    
- `until` → runs **until condition becomes true**
    

### Example

```bash
until [[ -f file.txt ]]; do
    echo "waiting for file.txt"
    sleep 1
done
```

---

## Summary

This section introduced:

- File permissions and copying
    
- Variables and quoting rules
    
- Loops and conditionals
    
- User input and arguments
    
- Functions and script composition
    
- Process control and file testing
    

These concepts form the foundation of real-world Bash scripting.