### Usage Scenario

Run builds on Windows node in Kubernetes cluster

### How to Set Up

Windows requires that the [OS version of your image needs to be compatible with that of worker node](https://docs.microsoft.com/en-us/virtualization/windowscontainers/deploy-containers/version-compatibility?tabs=windows-server-1903%2Cwindows-10-1909). For instance, worker node of OS version 1903 can only run images with OS version 1903 or earlier. To get OS version of worker node: 

1. Run below command to get the build number:

  ```
  kubectl get node <node name> -o jsonpath={.status.nodeInfo.kernelVersion} | awk -F'.' '{print $3}'
  ```
1. Map build number to OS version with below table:

  |Build Number | OS Version |
  |---|---|
  |18363|1909|
  |18362|1903|
  |17763|1809|
  |17134|1803|
  |16299|1709|
  |14393|1607|