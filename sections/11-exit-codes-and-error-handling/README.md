# Exit Codes and Error Handling

## Overview
Every command returns an exit status. A status of 0 indicates success, while anything else signals an error. Properly handling these codes is important for reliable scripts. Bash's `trap` command can respond to signals or errors.

## Detailed Explanation
The exit status of the last command is stored in `$?`. Scripts can exit explicitly using `exit <status>`. To stop a script when a command fails, you can check `$?` or use `set -e` to automatically exit on non-zero statuses. The `trap` builtin sets commands to run when the script receives signals (like `SIGINT`) or exits.

Example trap setup:
```bash
trap 'echo "An error occurred" >&2' ERR
trap 'echo "Cleaning up"' EXIT
```
`ERR` triggers when a command fails (with `set -e`), and `EXIT` runs at the end regardless of success.

## Code Examples
```bash
#!/bin/bash
set -e
trap 'echo "Failed on line $LINENO"' ERR

echo "Copying file"
cp missing.txt /tmp/
echo "This line will not run if cp fails"
```

## Common Pitfalls & Warnings
- Using `set -e` without understanding which commands may fail can cause unexpected exits.
- Forgetting to propagate exit codes when calling external commands or subscripts.

## Best Practices
- Return meaningful exit codes from your scripts (0 for success, >0 for errors).
- Use traps to clean up temporary files or handle interrupts gracefully.

## Mini Exercise
Write a script that tries to create a directory, reporting an error if it already exists (exit code 1) and success otherwise.
