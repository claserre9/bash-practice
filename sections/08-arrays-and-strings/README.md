# Arrays and Strings

## Overview
Bash supports indexed arrays, which are useful for grouping related values. String manipulation features let you slice, replace, and analyze text within variables.

## Detailed Explanation
Arrays are declared with parentheses: `arr=(one two three)`. Access elements using `${arr[0]}`. You can add elements by index or with `arr+=(four)`. To iterate over all elements, use `"${arr[@]}"`.

String manipulation includes length `${#var}`, substring extraction `${var:offset:length}`, and pattern removal `${var#pattern}` or `${var%pattern}`. These features help parse filenames or user input without external tools.

## Code Examples
```bash
colors=(red green blue)
echo "First color: ${colors[0]}"
colors+=(yellow)
for c in "${colors[@]}"; do
    echo "$c"
done

text="hello world"
echo "Length: ${#text}"
echo "Substring: ${text:0:5}"
echo "Remove prefix: ${text#hel}"
```

## Common Pitfalls & Warnings
- Accessing an unset array element returns an empty string, which may be unexpected.
- Quoting `${arr[@]}` vs `${arr[*]}` changes how elements expand—`@` preserves each element.

## Best Practices
- Always quote array expansions: `"${arr[@]}"` to handle spaces correctly.
- Use parameter expansion for simple string manipulations before resorting to external tools.

## Mini Exercise
Create an array of five animal names. Write a loop that prints each name in uppercase letters using parameter expansion.
