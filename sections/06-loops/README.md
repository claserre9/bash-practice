# Loops

## Overview
Loops allow scripts to repeat actions. Bash offers `for`, `while`, and `until` loops, with optional `break` and `continue` controls. Mastering loops is fundamental for automation and data processing.

## Detailed Explanation
- `for` loops iterate over a list of items: `for item in list; do ... done`.
- `while` loops run as long as a command or condition is true: `while condition; do ... done`.
- `until` loops are the inverse, running until a condition becomes true.

`break` exits the loop immediately, while `continue` skips to the next iteration. Loop variables are local to the loop unless explicitly exported.

## Code Examples
```bash
# Simple for loop
for file in *.log; do
    echo "Processing $file"
done

# While loop reading lines from a file
count=0
while read -r line; do
    echo "$line"
    ((count++))
done < myfile.txt

echo "Total lines: $count"
```

## Common Pitfalls & Warnings
- Forgetting `do` or `done` will cause syntax errors.
- Using `for file in *` without quotes can break on spaces or special characters.

## Best Practices
- Quote variables like `$file` inside loops to handle spaces correctly.
- Use `break` sparingly and document why a loop exits early.

## Mini Exercise
Create a script that loops through the numbers 1 to 5 and prints whether each number is odd or even.
