# File and Directory Handling

## Overview
Managing files and directories is a central task in scripting. Bash provides built-in tests and external tools like `find`, `basename`, and `dirname` to manipulate paths and check file properties.

## Detailed Explanation
Use the `test` command or `[ ]` to check conditions:
- `-f file` checks for a regular file.
- `-d dir` checks for a directory.
- `-r file`, `-w file`, `-x file` check read, write, and execute permissions.

`find` searches directories recursively, allowing filters by name, size, or modification time. `basename` strips directory paths from filenames, while `dirname` returns the directory portion.

## Code Examples
```bash
if [ -d "$1" ]; then
    echo "Directory exists"
else
    echo "No directory" >&2
fi

for f in $(find . -name '*.log'); do
    echo "Found log: $(basename "$f") in $(dirname "$f")"
done
```

## Common Pitfalls & Warnings
- Using `find` without quotes around patterns can lead to shell globbing.
- Forgetting to escape spaces in file paths causes errors.

## Best Practices
- Quote variables containing paths.
- Combine `find` with `-exec` or `xargs` for efficient batch operations.

## Mini Exercise
Write a script that lists all regular files under the current directory and prints their sizes in human-readable form using `du -h`.
