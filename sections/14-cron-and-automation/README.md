# Cron and Automation

## Overview
Cron is a scheduling system that automates command execution at specified times. Combined with `at` for one-time tasks, cron allows for recurring jobs such as backups, updates, and monitoring.

## Detailed Explanation
Cron jobs are defined in crontab files. Edit your crontab with `crontab -e`. The format is:
```
* * * * * command
- - - - -
| | | | |
| | | | +---- Day of week (0-7)
| | | +------ Month (1-12)
| | +-------- Day of month (1-31)
| +---------- Hour (0-23)
+------------ Minute (0-59)
```
Logs typically go to `/var/log/cron` or are emailed to the user. The `at` command schedules a job for a specific time, e.g., `echo "backup.sh" | at 02:00`.

## Code Examples
```bash
# Run a script every day at 3 AM
0 3 * * * /home/user/backup.sh
```

To list cron jobs:
```bash
crontab -l
```

## Common Pitfalls & Warnings
- Environment variables may differ in cron; specify full paths to commands.
- Forgetting to redirect output can cause mails to accumulate.

## Best Practices
- Test scripts manually before scheduling them.
- Use absolute paths and capture output to log files for troubleshooting.

## Mini Exercise
Create a crontab entry that runs `date >> ~/cron.log` every minute. Monitor the file to confirm entries are appended.
