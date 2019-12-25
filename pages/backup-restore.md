# Backup and Restore
------

### Database Backup

OneDev database can be backed up via database backup page in administration menu. Database auto-backup can also be scheduled here.

### Database Restore

To restore database from an existing backup file, stop OneDev and run below command:
```
/path/to/onedev/bin/restore.(sh|bat) /path/to/backup-file
```

### Repository Backup

The folder _/path/to/onedev/site_ contains git repositories, attachments and other important information. It should be backed up periodically.