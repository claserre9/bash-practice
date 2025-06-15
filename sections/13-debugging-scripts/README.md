# Debugging Scripts

## Overview
Debugging helps identify issues in your scripts. Bash offers options like `set -x` for tracing, `set -e` to stop on errors, and manual echo statements for inspection.

## Detailed Explanation
- **Tracing**: `set -x` prints each command and its arguments as they execute. Turn it off with `set +x`.
- **Error checking**: `set -e` exits the script on any command returning a non-zero status. Use with care.
- **Verbose mode**: Some scripts provide a verbose option to print internal state using `echo` or custom logging functions.

You can also run scripts with `bash -x script.sh` to enable tracing without modifying the script itself.

## Code Examples
```bash
#!/bin/bash
set -xe  # trace and exit on error

cp file1.txt /tmp/
rm /tmp/file1.txt
```

## Common Pitfalls & Warnings
- Leaving `set -x` enabled in production scripts can clutter output and reveal sensitive data.
- `set -e` may cause unexpected exits when used with commands that legitimately return non-zero statuses.

## Best Practices
- Isolate complex commands and test them separately.
- Use meaningful log messages when tracing variables or execution flow.

## Mini Exercise
Run a simple script with `bash -x` to observe the order of command execution. Try adding `set -e` and intentionally causing an error to see how the script stops.
