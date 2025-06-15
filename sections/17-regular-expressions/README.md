# Regular Expressions

## Overview
Regular expressions (regex) are patterns used to match strings. Bash leverages tools like `grep` and `sed`, and the `[[ =~ ]]` operator, to perform regex matching and text extraction.

## Detailed Explanation
`grep` searches for lines matching a pattern, supporting basic (`grep`) and extended (`grep -E`) regex. `sed` can substitute text using regex with `s/pattern/replacement/`. Inside Bash's `[[ ]]`, the `=~` operator allows regex matching without external tools, storing matches in `${BASH_REMATCH[@]}`.

Regex syntax includes literals, character classes `[a-z]`, quantifiers `*`, `+`, `{m,n}`, and anchors `^` and `$`. Extended regex adds features like `|` for alternation and parentheses for grouping.

## Code Examples
```bash
echo "hello" | grep -E 'h.*o'
string="file123.txt"
if [[ $string =~ ([a-z]+)([0-9]+) ]]; then
    echo "Name: ${BASH_REMATCH[1]}"
    echo "Number: ${BASH_REMATCH[2]}"
fi
```

## Common Pitfalls & Warnings
- Forgetting to quote regex patterns in commands can lead to shell glob expansion.
- Using `grep` without `-E` when you need extended features like `+` or `|`.

## Best Practices
- Test regex patterns with sample data before using them in scripts.
- Use `[[ =~ ]]` for simple matches; rely on `grep` or `sed` for complex processing.

## Mini Exercise
Create a script that extracts the domain name from an email address using `[[ =~ ]]` and prints it.
