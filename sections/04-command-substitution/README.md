# Command Substitution

## Overview
Command substitution allows you to capture the output of a command and use it as a variable or argument. Bash supports two forms: `$(command)` and the older backtick syntax ``command``.

## Detailed Explanation
When Bash encounters `$(command)`, it runs `command` in a subshell and replaces the substitution with the command's output, minus trailing newlines. This is useful for assigning command results to variables or embedding them in other commands. Backticks work similarly but can be harder to read and nest. Nested substitutions with `$(...)` are clearer and less error-prone.

Substitutions occur before variable assignment or command execution, so quoting is important to preserve spaces and newlines.

## Code Examples
```bash
now=$(date)
echo "Current time: $now"
files=$(ls *.txt)
for f in $files; do
    echo "Found $f"
done
```
Nested example:
```bash
echo "The number of lines: $(wc -l < "$(grep -l pattern *.txt | head -n 1)")"
```

## Common Pitfalls & Warnings
- Using backticks inside backticks is confusing; prefer `$(...)` for nesting.
- Omitting quotes around command substitutions can lead to word splitting.

## Best Practices
- Use `$(...)` instead of backticks for readability.
- Quote substitutions if the output may contain spaces or glob characters.

## Mini Exercise
Create a script that saves the current directory listing to a variable and prints the number of files using `wc -l` with command substitution.
