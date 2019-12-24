# Use External Database
-------

**Note this procedure is only applicable for [bare metal installation](run-on-bare-metal-machine.md).**

By default, OneDev uses the embedded HSQL database for demonstration purpose. For production usage, it is highly recommended to switch to external database for reliability and performance reason. OneDev can work with below databases:
* MySQL 5.0 or higher
* Oracle 9i or higher
* SQL Server 2008 or higher
* PostgreSQL 9.0 or higher
* MariaDB 5.0 or higher

To switch to use one of above databases, follow below steps:

1. Stop OneDev server by running _/path/to/onedev/bin/server.sh stop_ (or run server.bat on Windows)
1. Run command _/path/to/onedev/bin/backup.(sh|bat) /path/to/backup-file_ 
1. Edit file _/path/to/onedev/conf/hibernate.properties_ to comment out the HSQLDB section and uncomment the section of your desired external database. Also provide connection details to your database
1. Create a blank external database matching connection details of above step
1. Run command _/path/to/onedev/bin/restore.(sh|bat) /path/to/backup-file_
1. Start OneDev server and check if everything is fine

Procedure is the same if you want to switch to a different external database than current external database.