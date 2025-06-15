# STDIN, STDOUT, and STDERR

## Overview
Bash programs communicate via three standard streams: standard input (stdin), standard output (stdout), and standard error (stderr). Redirecting these streams and using pipes enables powerful command chaining.

## Detailed Explanation
- **Redirection**: `>` writes stdout to a file, `>>` appends, and `<` reads from a file. Use `2>` to redirect stderr and `&>` to capture both stdout and stderr.
- **Pipes**: `cmd1 | cmd2` connects stdout of `cmd1` to stdin of `cmd2`, allowing complex processing chains.
- **File descriptors**: stdin is 0, stdout is 1, stderr is 2. You can redirect or duplicate descriptors using syntax like `2>&1`.

By mastering redirection and pipes, you can control where output goes and use commands together efficiently.

## Code Examples
```bash
ls -l /nonexistent 1>out.txt 2>err.txt
cat out.txt
cat err.txt

echo "hello" | tr 'a-z' 'A-Z'

command > all.log 2>&1  # capture everything
```

## Common Pitfalls & Warnings
- Forgetting to quote file names in redirections can lead to unexpected filenames or globbing.
- Reversing `2>&1` and `>file` changes the order of redirections and may lose errors.

## Best Practices
- Use explicit redirections to control output location, especially in scripts.
- Consider logging stderr separately to troubleshoot problems.

## Mini Exercise
Write a command that runs `grep` on a file that doesn't exist, capturing stderr to `error.log` while discarding stdout.
