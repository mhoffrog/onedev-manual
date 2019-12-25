# Run on Bare Metal Machine

To achieve maximum flexibility, you may run OneDev on bare metal machine (this procedure also works if you are running OneDev on virtual machines)

### Installation

1. Make sure your system has Java 8 or higher installed. If not, download and install from [here](https://www.java.com/en/download/)
1. Make sure your system has git 2.11.1 or higher installed. For Windows, make sure to use [git for windows](https://git-for-windows.github.io/)
1. On Linux and Mac, make sure your system has [curl](https://curl.haxx.se) installed, you may run command _curl_ to verify
1. Select desired [OneDev release](https://code.onedev.io/projects/onedev-server/builds?query=%22Job%22+is+%22Release%22)  and download _onedev-<release>.zip_
1. Extract the downloaded file into the selected installation directory. Let's assume it to be _/opt/onedev_. Make sure the user running OneDev has *full access rights* to _/opt/onedev_
1. Open _/opt/onedev/conf/wrapper.conf_ to change below settings if necessary:
    * Modify property _wrapper.java.command_ to path of Java command if it does not exist in system path.
    * Open a command window, switch to folder _/opt/onedev/bin_, and run command _server.bat console_ (on Windows) or _server.sh console_ (on Unix/Linux/Mac) to start the server

### Post-install tasks (optional)

 * [Increase Ulimit](increase-ulimit.md)
 * [Run as System Service](run-as-system-service.md)
 * [Use External Database](use-external-database.md)