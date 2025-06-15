# Writing Robust Scripts

## Overview
Robust scripts handle errors gracefully, validate input, and use defensive programming techniques. They remain reliable under unexpected conditions and provide meaningful feedback when something goes wrong.

## Detailed Explanation
- **Input validation**: Check parameters and file existence before acting. Use regular expressions or built-ins like `test` to verify conditions.
- **Error handling**: Combine `set -e` or explicit status checks with descriptive messages. Trap signals to clean up temporary files or child processes.
- **Resilient logic**: Use `if` statements, loops, and case switches to anticipate failure scenarios. Avoid relying on global state when possible, and modularize code into functions.

Logging progress and errors to a file helps debugging after the script runs unattended.

## Code Examples
```bash
#!/bin/bash
set -euo pipefail
trap 'echo "Script failed" >&2' ERR

if [ $# -ne 1 ]; then
    echo "Usage: $0 directory" >&2
    exit 1
fi

if [ ! -d "$1" ]; then
    echo "Directory not found: $1" >&2
    exit 1
fi

echo "Processing $1"
```

## Common Pitfalls & Warnings
- Ignoring error codes allows failures to pass silently, leading to data loss or corruption.
- Overusing `set -e` without understanding can terminate scripts prematurely.

## Best Practices
- Combine `set -euo pipefail` for strict error checking.
- Keep functions small and focused; handle errors close to where they occur.

## Mini Exercise
Expand the example above to loop through all files in the directory and count lines, skipping files that cannot be read. Log any errors to `error.log`.
