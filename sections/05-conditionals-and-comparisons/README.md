# Conditionals and Comparisons

## Overview
Scripts often need to make decisions. Bash provides `if`, `else`, and `elif` statements for conditional logic. Comparisons are done with `test`, `[ ]`, or `[[ ]]` for advanced features.

## Detailed Explanation
The basic syntax is:
```bash
if condition; then
    commands
elif other_condition; then
    other_commands
else
    fallback_commands
fi
```
`test` or `[ ]` evaluate expressions such as file existence (`-f file`) or string comparison (`=`, `!=`). The double-bracket `[[ ]]` is a Bash extension offering pattern matching and safer string handling.

Numeric comparisons use `-eq`, `-ne`, `-gt`, `-lt`, etc. String comparisons use `=` or `!=`. For arithmetic, you can also use `(( ))`.

## Code Examples
```bash
if [ -f "$1" ]; then
    echo "File exists"
else
    echo "File not found"
fi

num=5
if [[ $num -gt 3 && $num -lt 10 ]]; then
    echo "Within range"
fi
```

## Common Pitfalls & Warnings
- Forgetting spaces inside `[ ]` will cause syntax errors.
- Using single `[` with `==` for pattern matching may behave differently across shells; use `[[` in Bash.

## Best Practices
- Quote variables inside tests to avoid globbing or word splitting.
- Use `[[ ]]` for string comparisons in Bash scripts for added safety.

## Mini Exercise
Write a script that checks if a provided argument is a directory. If so, print the number of files inside; otherwise, print an error message.
