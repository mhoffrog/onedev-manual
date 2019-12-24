# Backup and Restore
------

### Database Backup

OneDev database can be backed up via database backup page in administration menu. Optionally you can also run below command to do database backup when OneDev is stopped:
```
/path/to/onedev/bin/backup.(sh|bat) /path/to/backup-file 
```
Database auto-backup can also be scheduled in database backup page of administration menu.

### Database Restore

To restore database from an existing backup file, stop OneDev and run below command:
```
/path/to/onedev/bin/restore.(sh|bat) /path/to/backup-file
```

### Site Directory Backup

The folder _/path/to/onedev/site_ contains git repositories, attachments and other important information. It should be backed up periodically.