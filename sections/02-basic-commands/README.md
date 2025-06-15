# Basic Commands

## Overview
Before diving into scripting, it's essential to know common shell commands. `echo`, `pwd`, `cd`, `ls`, `mv`, `cp`, and `rm` form the backbone of daily terminal usage. These commands help navigate directories, list contents, and manipulate files.

## Detailed Explanation
- `echo` prints text to standard output, often used for messages or variable values.
- `pwd` displays the current directory path.
- `cd` changes directories; running `cd` with no arguments returns to your home directory.
- `ls` lists directory contents with options like `-l` for long format or `-a` to show hidden files.
- `mv` moves or renames files and directories.
- `cp` copies files or directories with the `-r` option for recursion.
- `rm` removes files or directories (use `-r` for directories and `-i` for interactive confirmation).

Understanding these commands is crucial for building scripts that interact with the filesystem.

## Code Examples
```bash
pwd               # show current directory
ls -l             # long listing format
cd /tmp           # change to /tmp directory
echo "Listing contents:" && ls
cp file1.txt backup.txt
mv backup.txt archive.txt
rm archive.txt
```

## Common Pitfalls & Warnings
- Using `rm` without caution can delete important data—consider `rm -i` for prompts.
- Forgetting quotes around paths with spaces will cause errors.

## Best Practices
- Combine commands with logical operators like `&&` to ensure proper sequencing.
- Use clear file names and backup before bulk operations.

## Mini Exercise
Create a directory called `playground`, copy `/etc/hosts` into it as `hosts.bak`, then remove the copy.
