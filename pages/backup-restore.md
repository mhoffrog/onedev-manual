# Backup and Restore
------

### Database Backup

OneDev database can be backed up via database backup page in administration menu. Database auto-backup can also be scheduled here.

Database can also be backed up in [maintenance mode](maintenance-mode.md) by running (assume OneDev is installed in _/opt/onedev_):
```
/opt/onedev/bin/backup-db.(sh|bat) /path/to/backup.zip
```

### Database Restore

To restore database from an existing backup file, run below command in [maintenance mode](maintenance-mode.md) (assume OneDev is installed in _/opt/onedev_):
```
/opt/onedev/bin/restore-db.(sh|bat) /path/to/backup.zip
```

### Repository Backup

The folder _/opt/onedev/site_ (assume OneDev is installed in _/opt/onedev_) contains git repositories, attachments and other important data. It should be backed up periodically. You may use some volume backup tools or file sync tools for this purpose.