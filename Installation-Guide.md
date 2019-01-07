### Supported operating systems

OneDev requires Java 8 or higher, and git 1.9.0 or higher. It should be able to run on any operating systems supporting these two tools. We officially tested OneDev on below systems:

* Windows, 64bit
* Linux, 64bit
* Mac OS X, 64 bit

### Supported browsers
* Internet Explorer 11 or higher
* Microsoft Edge 
* Firefox 40.0 or higher
* Safari 7.0 or higher
* Chrome 40.0 or higher

### Memory requirement

Your system running OneDev should have at least 2G physical memory. If you have many large git repositories, you will need more memory. 

### Installation Steps

1. Make sure your system has Java 8 or higher installed. If not, download and install from [here](https://www.java.com/en/download/)
1. Make sure your system has git 1.9.0 or higher installed. For Windows, make sure to use [git for windows](https://git-for-windows.github.io/)
1. On Linux and Mac, make sure your system has [curl](https://curl.haxx.se) installed, you may run command _curl_ to verify
1. Download OneDev distribution [here](https://github.com/theonedev/onedev/releases)
1. Extract the downloaded file into the selected installation directory. Make sure the user running OneDev has *full access rights* to the installation directory
1. Open _/path/to/onedev/conf/wrapper.conf_ to change below settings if necessary:
    * Modify property _wrapper.java.command_ to path of Java 8 command if it does not exist in system path
   By default OneDev uses half of your system memory. If this is not what you want, uncomment property _wrapper.java.maxmemory_ to specify an appropriate value
    * Open a command window, switch to folder _/path/to/onedev/bin_, and run command _server.(bat|sh) console_ to start the server
    * Monitor the console window for any error or warning messages
    * After the server starts up, follow the instruction in the console to open a browser window and connect to the server to continue with server set up.

### Further Reading

Below steps are not necessary for first-time set up, but you may want to check them out for production use:
 * [Run as System Service](Run-As-System-Service)
 * [Use External Database](Use-External-Database)
 * [Reverse Proxy Set Up](Reverse-Proxy-Setup)
 * [Security Management](Security-Management)
 * [Increase Ulimit](Increase-Ulimit)
