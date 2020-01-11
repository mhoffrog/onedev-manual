This document explains how to configure OneDev to run as system service so that it runs in the backend and can start automatically when system starts. We assume that OneDev is installed at _C:\\onedev_ on Windows and _/opt/onedev_ on Linux/Mac

### On Windows Platform
1. Edit file _C:\\onedev\\conf\\wraper.conf_ to set value of property _wrapper.java.command_ as path to java command

1. [Open a command prompt with administrator privilege](https://www.howtogeek.com/194041/how-to-open-the-command-prompt-as-administrator-in-windows-8.1/) and switch to folder _C:\\onedev\\bin_

1. Run command `server.bat install`, and a Windows service with name _OneDev_ will be installed

1. To uninstall the service, run command `server.bat remove` from the same folder with administrator privilege

### On Linux and Mac OS X

1. Edit file _/opt/onedev/conf/wraper.conf_ to set value of property _wrapper.java.command_ as path to java command

1. By default, the service will run under root user. To run as another user, edit file _/opt/onedev/bin/server.sh_ and uncomment below line to specify the user. Make sure specified user has full permission over _/opt/onedev_ and all its sub directories:

  ```
  #RUN_AS_USER=
  ```

1. Run command `/opt/onedev/bin/server.sh install` as root user to install the service

1. To uninstall the service, run command `/opt/onedev/bin/server.sh remove` as root user