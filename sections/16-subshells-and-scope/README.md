# Subshells and Scope

## Overview
Subshells are child processes created by Bash for certain operations, such as command substitution or grouping commands with parentheses. Understanding subshell behavior helps control variable scope and performance.

## Detailed Explanation
Commands inside `( ... )` run in a subshell, meaning any variable changes do not affect the parent shell. Conversely, `{ ...; }` runs commands in the current shell when used with proper spacing and a trailing semicolon. Pipelines also spawn subshells for each stage in POSIX shells, though Bash may optimize when possible.

Knowing which constructs spawn a subshell is crucial when you expect variables to persist after a command. Forking a subshell can have performance costs but isolates environment changes.

## Code Examples
```bash
count=1
(count=5)
echo $count  # still 1

{
    count=5
}
echo $count  # now 5
```

## Common Pitfalls & Warnings
- Expecting variables set in a subshell (e.g., within parentheses or pipelines) to persist in the main shell.
- Forgetting the semicolon before `}` when grouping commands.

## Best Practices
- Use `{ }` when you need to group commands without spawning a subshell.
- Be mindful of performance when creating many subshells in loops or scripts.

## Mini Exercise
Write a script that modifies a variable inside both a subshell and a grouped command. Observe which change persists after each block.
