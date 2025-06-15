# Script Arguments

## Overview
Scripts often need to accept user-provided parameters. Bash exposes positional parameters `$1`, `$2`, ..., while `$#` gives the number of arguments and `$@` or `$*` expand to all arguments. The `getopts` builtin helps parse options.

## Detailed Explanation
Positional parameters are accessed by number. `$@` expands each argument as a separate word when quoted (`"$@"`), preserving spaces. `$*` joins them into a single word. To process flags like `-h` or `-f file`, use `getopts`:
```bash
while getopts "f:v" opt; do
    case $opt in
        f) file=$OPTARG ;;
        v) verbose=1 ;;
        *) echo "Usage: $0 [-v] [-f file]" ; exit 1 ;;
    esac
done
shift $((OPTIND - 1))
```
Validating arguments prevents errors and improves user experience.

## Code Examples
```bash
#!/bin/bash
if [ $# -lt 1 ]; then
    echo "Usage: $0 filename" >&2
    exit 1
fi

file=$1
echo "Processing $file"
```

## Common Pitfalls & Warnings
- Forgetting to reset `OPTIND` when calling `getopts` multiple times in the same script.
- Not quoting `$@` can break arguments containing spaces.

## Best Practices
- Provide helpful usage messages when arguments are missing or incorrect.
- Use `getopts` for parsing short options to keep scripts POSIX-compliant.

## Mini Exercise
Create a script that accepts two arguments: a filename and a word. The script should count occurrences of the word in the file and print the result.
