# Variables and Quotes

## Overview
Bash variables store data for later use. Understanding quoting rules is essential to preserve or expand variable values correctly. Escaping characters allows you to handle special symbols safely.

## Detailed Explanation
Variables are created by assigning a value: `name="Alice"`. No spaces around the equals sign are allowed. To access the value, prefix the variable with `$`, like `$name`. Quotes influence how Bash interprets special characters:
- **Double quotes** allow variable expansion: `echo "$name"` prints the value.
- **Single quotes** prevent expansion: `echo '$name'` prints the literal text `$name`.
- **Escaping** with backslashes (`\`) lets you include special characters.

Use curly braces `${var}` when adjacent text might confuse the interpreter.

## Code Examples
```bash
name="Alice"
echo $name       # Alice
echo "$name"    # Alice with double quotes
path="/tmp/${name}_data"  # braces make the variable clear
echo 'User is $name'  # single quotes prevent expansion
```

## Common Pitfalls & Warnings
- Leaving spaces around `=` when assigning variables results in command errors.
- Forgetting quotes around variable expansions can cause word splitting or globbing.

## Best Practices
- Quote variables unless you specifically want word splitting or filename expansion.
- Prefer lowercase variable names for local script variables to avoid conflicts with environment variables.

## Mini Exercise
Write a script that sets a variable `greeting` to `Hello`, then prints `Hello, <your name>` using that variable and a second variable `name`.
