# Run on Bare Metal Machine

To achieve maximum flexibility, you may run OneDev on bare metal machine (this procedure also works if you are running OneDev on virtual machines)

### Installation

1. Make sure your system has [Java 8 or higher](https://www.oracle.com/technetwork/java/javase/downloads/index.html) installed and available in system path 
1. Make sure your system has [git 2.11.1 or higher](https://git-scm.com/downloads) installed and available in system path
1. On Linux and Mac, make sure your system has [curl](https://curl.haxx.se) installed and available in system path
1. Select desired [**OneDev release**](https://code.onedev.io/projects/onedev-server/builds?query=%22Job%22+is+%22Release%22)  and download `onedev-<release>.zip`
1. Extract downloaded file into selected installation directory. Make sure current user has *full permissions* to the directory and all its sub directories
1. Open a command prompt, change to the installation directory, and run command _server.bat console_ (on Windows) or _./server.sh console_ (on Unix/Linux/Mac) to start the server

### Post-install tasks (optional)

 * [Increase Ulimit](increase-ulimit.md)
 * [Run as System Service](run-as-system-service.md)
 * [Use External Database](use-external-database.md)