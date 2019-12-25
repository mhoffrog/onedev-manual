This document explains how to configure OneDev to run as system service so that it runs in the backend and can start automatically when system starts. We assume that OneDev is installed at _/opt/onedev_

### On Windows Platform
1. If necessary, edit file _/opt/onedev/conf/wrapper.conf_ to specify service account via below properties:
  ```
  wrapper.ntservice.account=
  wrapper.ntservice.password=
 ```
The service will run under local system account if these properties are not specified.
1. Open a command prompt window and switch to folder _/opt/onedev/bin_. On Windows system with UAC enabled, you will need to [open the command prompt window as Administrator](http://www.howtogeek.com/howto/windows-vista/run-a-command-as-administrator-from-the-windows-vista-run-box/) 
1. Run command `server.bat install` from command prompt window, and a Windows service with the name _OneDev_ will be installed.
1. If you want to uninstall the service later, just run command `server.bat remove` from the command prompt window (make sure the command prompt window is [opened with administrative right](http://www.howtogeek.com/howto/windows-vista/run-a-command-as-administrator-from-the-windows-vista-run-box/) on Windows system with UAC enabled).

### On Linux and Mac OSX
1. Open a command shell and switch to folder _/opt/onedev/bin_
1. Edit file _server.sh_ to uncomment below line to specify the OS user to run the service as. Make sure the user has full permission against OneDev installation directory including all sub directories and files
  ```
  #RUN_AS_USER=
  ```
1. The service will be run under root account if this line is commented out
1. Run command `./server.sh install` to install the service
1. If you want to uninstall the service later, just run command `./server.sh remove` from the command shell