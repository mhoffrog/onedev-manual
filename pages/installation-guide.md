# Installation Guide
----------

### Supported operating systems

OneDev requires Java 8 or higher, and git 2.11.1 or higher. It should be able to run on any operating systems supporting these two tools. We officially tested OneDev on below systems:

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

### Run as Docker Container

This is the simplest approach to get OneDev up and running. To do it, run below command in Linux environment:
```
docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker -v /opt/onedev:/opt/onedev -p 6610:6610 1dev/server
```
[More on running as docker container](running-as-docker-container.md)

### Deploy into Kubernetes Cluster

1. Select desired [OneDev release](https://code.onedev.io/projects/onedev-server/builds?query=%22Job%22+is+%22Release%22)  and download _k8s-resources.zip_
2. Unzip the file, change into directory _production_, modify node selectors, memory setting and disk setting if necessary, and then run below command from this directory:
  ```
  kubectl apply -k .
  ```
3. OneDev resources will be created under namespace _onedev_. Wait a while for pods in this namespace to be up and running. Then access ip address assigned by onedev load balancer to access OneDev. For instance on Google Kubernetes Engine, one can access OneDev server this way:

 ![K8s Access Onedev](k8s-access-onedev.png)
 
[More on Kubernetes deployment](kubernetes-deployment.md)

### Install on Bare Metal Machine

To achieve the maximum flexibility, you may install OneDev on bare metal machine:

1. Make sure your system has Java 8 or higher installed. If not, download and install from [here](https://www.java.com/en/download/)
1. Make sure your system has git 2.11.1 or higher installed. For Windows, make sure to use [git for windows](https://git-for-windows.github.io/)
1. On Linux and Mac, make sure your system has [curl](https://curl.haxx.se) installed, you may run command _curl_ to verify
1. Select desired [OneDev release](https://code.onedev.io/projects/onedev-server/builds?query=%22Job%22+is+%22Release%22)  and download _onedev-<release>.zip_
1. Extract the downloaded file into the selected installation directory. Let's assume it _/opt/onedev_. Make sure the user running OneDev has *full access rights* to the installation directory
1. Open _/opt/onedev/conf/wrapper.conf_ to change below settings if necessary:
    * Modify property _wrapper.java.command_ to path of Java command if it does not exist in system path.
    * Open a command window, switch to folder _/opt/onedev/bin_, and run command _server.bat console_ (on Windows) or _server.sh console_ (on Unix/Linux/Mac) to start the server

[More on bare metal installation](bare-metal-installation.md)