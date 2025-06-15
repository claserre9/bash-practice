# Scripting Patterns

## Overview
Beyond simple one-liners, scripts often follow patterns for interaction, configuration, or user input. Techniques such as building menus and reading config files make scripts more user-friendly and maintainable.

## Detailed Explanation
- **Interactive menus**: `select` provides a simple menu system. You can also use loops with case statements to prompt users.
- **Configuration files**: Storing settings in a file (e.g., key=value pairs) allows scripts to be customized without editing the code. Use `source config.conf` to load variables.
- **Logging and verbosity**: Implement functions to print messages with different levels (info, warning, error) and optionally redirect to log files.

These patterns help build larger scripts in an organized manner.

## Code Examples
```bash
# Simple menu
PS3="Choose an option: "
select choice in Start Stop Quit; do
    case $REPLY in
        1) echo "Starting" ;;
        2) echo "Stopping" ;;
        3) break ;;
    esac
done

# Loading a config file
if [ -f my.conf ]; then
    source my.conf
fi
```

## Common Pitfalls & Warnings
- Relying solely on `select` can be limiting; handle invalid input with care.
- Sourcing untrusted configuration files may execute unintended commands.

## Best Practices
- Validate user input in menus and provide clear prompts.
- Separate configuration from code to make scripts easier to maintain.

## Mini Exercise
Create a script that loads a config file with a variable `TARGET_DIR` and then offers a menu to copy or move files into that directory.
