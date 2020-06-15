# Admin tasks

## /tmp cleaning

Find files in `/tmp` older than 10 days and delete them.

```bash
sudo find /tmp -type f -atime +10 -delete
```
