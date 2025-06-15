# Parsing Text

## Overview
Bash scripts frequently process text files and command output. Tools like `awk`, `sed`, `cut`, `head`, `tail`, and `tr` allow you to extract and transform data efficiently.

## Detailed Explanation
- **awk**: A powerful language for pattern scanning and processing. Use it to select columns, perform calculations, and apply conditions.
- **sed**: Stream editor useful for substitutions and simple transformations.
- **cut**: Extract specific fields or character ranges from each line.
- **head/tail**: View the beginning or end of files.
- **tr**: Translate or delete characters, often for case conversion or cleanup.

Combining these tools in pipelines creates flexible text processing workflows.

## Code Examples
```bash
awk -F: '{print $1}' /etc/passwd | head

echo "one,two,three" | tr ',' '\n'

echo "name=value" | cut -d'=' -f2
```

## Common Pitfalls & Warnings
- Using `sed -i` without backups can overwrite files irreversibly.
- `cut` relies on consistent delimiters; irregular input may produce unexpected results.

## Best Practices
- Test commands on sample data before running them on important files.
- Use awk scripts or functions for complex parsing instead of convoluted pipelines.

## Mini Exercise
Write a one-liner that prints the second column of `/etc/passwd`, sorted uniquely, using `cut` and `sort`.
