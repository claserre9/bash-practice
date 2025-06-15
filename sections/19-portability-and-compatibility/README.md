# Portability and Compatibility

## Overview
Scripts may need to run on different systems or shells. Writing portable code ensures your scripts work in POSIX environments, while understanding Bash-specific features lets you take advantage of enhanced capabilities when available.

## Detailed Explanation
- **POSIX compliance**: Stick to standard shell syntax (e.g., use `#!/bin/sh`) and avoid Bash-only constructs if portability is required. POSIX shells lack arrays and the `[[ ]]` test command.
- **Bash-only features**: Arrays, associative arrays, `[[ ]]`, `(( ))`, and here-strings (`<<<`) are not available in strictly POSIX shells. If you rely on them, set the shebang to `#!/bin/bash`.
- **Detecting Bash**: Scripts can check `BASH_VERSION` to alter behavior when run under Bash versus another shell.

Balancing portability with convenience depends on your deployment environment.

## Code Examples
```bash
#!/bin/sh
# Portable example
if [ "$1" = "hello" ]; then
    echo "Hi"
fi
```
Bash-only example:
```bash
#!/bin/bash
arr=(one two)
echo "${arr[1]}"
```

## Common Pitfalls & Warnings
- Using Bash extensions under `/bin/sh` may fail on systems where `/bin/sh` is not Bash.
- Relying on GNU options for commands like `sed` or `grep` may break on BSD or macOS versions.

## Best Practices
- Decide upfront whether portability or Bash features are more important for your script.
- Test scripts on multiple environments when portability is a goal.

## Mini Exercise
Modify a Bash-specific script to run in `/bin/sh` by replacing arrays with plain variables and adjusting syntax.
