# Backup and Restore
--------------

OneDev stores its data in two places:
* database
   
  Database contains metadata such as project information, user information, pull request information etc.
  
* storage directory

  Storage directory contains git repositories, index data, attachment etc. 

### Database Backup

Besides the git repository data in storage directory, OneDev also stores additional information such as user, organization, pull requests, and reviews into database.

OneDev database can be backed up via database backup page in administration menu like below:

![database-backup.png](images/database-backup.png)

From this page, you can either schedule auto-backups, or click the _backup now_ button to do a one-time backup. Optionally you can also run below command to do database backup when OneDev is stopped:
```
/path/to/onedev/bin/backup.(sh|bat) /path/to/backup-file 
```

### Database Restore

To restore database from an existing backup file, stop OneDev and run below command:
```
/path/to/onedev/bin/restore.(sh|bat) /path/to/backup-file
```

### Storage Directory Backup/Restore

Any backup tool able to handle file system backup can be used to backup/restore the storage directory.