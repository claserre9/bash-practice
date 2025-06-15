# Functions

## Overview
Functions group commands into reusable blocks. They help organize scripts and reduce repetition. Understanding scope and return values is key to building maintainable scripts.

## Detailed Explanation
Define a function using either `name() { commands; }` or the older `function name { commands; }` syntax. Arguments inside functions are referenced as `$1`, `$2`, etc., separate from the script's arguments. Use `return` to provide an exit status (0–255). Variables declared inside functions are global by default; to limit scope, use the `local` keyword.

Functions can be defined anywhere in the script, but placing them near the top improves readability. Calling a function is simply writing its name with optional arguments.

## Code Examples
```bash
#!/bin/bash
print_greeting() {
    local name=$1
    echo "Hello, $name"
    return 0
}

print_greeting "Alice"
status=$?
echo "Function exited with status $status"
```

## Common Pitfalls & Warnings
- Forgetting `local` can lead to variable collisions between functions.
- Exiting from inside a function with `exit` will terminate the entire script.

## Best Practices
- Use descriptive function names and keep them short.
- Place all function definitions before the main script logic for clarity.

## Mini Exercise
Write a function `sum()` that takes two numbers and echoes their sum. Call it with different pairs of numbers.
