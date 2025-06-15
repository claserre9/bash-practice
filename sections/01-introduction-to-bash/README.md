# Introduction to Bash

## Overview
Bash (Bourne Again SHell) is a widely used command-line interpreter found on most Unix-like systems. It allows you to run commands interactively in a terminal or execute entire scripts. Learning Bash opens the door to automating tasks, managing systems, and building portable scripts.

## Detailed Explanation
Bash is both an interactive shell and scripting language. When you start a terminal, Bash reads configuration files and presents a prompt. A script is simply a text file containing commands. The first line often begins with a *shebang*, like `#!/bin/bash`, which tells the system what interpreter to use. Running commands manually versus executing a script can have different environments, so understanding both modes is key.

Scripts can be launched by specifying the interpreter (`bash script.sh`) or by making the file executable (`chmod +x script.sh`) and running `./script.sh`. When you run commands from a terminal, they execute in the current shell; scripts run in their own process by default.

## Code Examples
```bash
#!/bin/bash
# hello.sh - a simple script

echo "Hello, world!"
```
Run it with:
```bash
chmod +x hello.sh
./hello.sh
```

## Common Pitfalls & Warnings
- Forgetting the shebang can cause scripts to run in the wrong shell.
- Windows line endings (`\r\n`) may cause errors; use Unix line endings (`\n`).

## Best Practices
- Always include a shebang at the top of scripts.
- Make scripts executable and store them with consistent permissions.
- Use comments to describe what your script does.

## Mini Exercise
Create a script named `greet.sh` that prints `Hello` followed by your username (use the `$USER` variable). Make it executable and run it.
