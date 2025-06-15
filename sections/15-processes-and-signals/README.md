# Processes and Signals

## Overview
Bash interacts with running programs as processes. Commands like `ps` and `kill` manage them, while `trap` allows scripts to respond to signals. Background jobs enable multitasking within the shell.

## Detailed Explanation
`ps` lists running processes; `ps aux` shows all processes. Use `kill PID` to send signals, typically `SIGTERM` (15) or `SIGKILL` (9). Signals notify processes of events like termination or hangup. Within scripts, `trap` can catch signals to perform cleanup:
```bash
trap 'echo "Interrupted"; cleanup' INT
```
Background jobs are started with `&`. Use `jobs` to list them and `fg` or `bg` to move them between the foreground and background.

## Code Examples
```bash
sleep 60 &  # start a background job
jobs
kill %1      # send SIGTERM to job 1

trap 'echo "Stopping"' TERM
while true; do
    sleep 5
done
```

## Common Pitfalls & Warnings
- Sending `SIGKILL` prevents the process from cleaning up resources.
- Forgetting to quote variables in `trap` commands may cause unexpected behavior.

## Best Practices
- Handle signals gracefully with `trap` to remove temporary files or stop child processes.
- Use `kill -l` to list available signals and choose appropriate ones for your scripts.

## Mini Exercise
Write a script that runs a background process (e.g., `sleep 30`) and traps `SIGINT` to print a message before exiting.
