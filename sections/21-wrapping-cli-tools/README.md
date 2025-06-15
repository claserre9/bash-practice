# Wrapping CLI Tools

## Overview
Bash scripts often act as wrappers around other command-line programs such as `git`, `curl`, or `docker`. Wrapping tools can simplify repetitive tasks or enforce consistent options across a team.

## Detailed Explanation
A wrapper script typically sets default arguments, handles environment preparation, or chains multiple commands. For example, you might create `git-cleanup.sh` that runs a sequence of `git` commands. Use functions to modularize actions and provide helpful usage messages.

Capturing command output or exit codes allows the wrapper to react accordingly—for instance, retrying a failed network request with `curl`.

## Code Examples
```bash
#!/bin/bash
set -e

run_curl() {
    curl -fsSL "$@"
}

echo "Downloading file"
run_curl https://example.com/file.txt -o file.txt
```

## Common Pitfalls & Warnings
- Blindly passing user input to wrapped commands can introduce security risks.
- Hardcoding command paths may break on systems where tools are installed in different locations.

## Best Practices
- Validate arguments before passing them to the underlying tool.
- Provide clear error messages and exit codes when the wrapped command fails.

## Mini Exercise
Write a wrapper script around `docker run` that always sets a specific network and volume mount. Allow additional arguments to be passed through to `docker`.
