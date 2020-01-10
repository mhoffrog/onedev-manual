### Usage Scenario

Run builds on Windows node in Kubernetes cluster

### How to Set Up

Windows requires that the [OS version of your image needs to be compatible with that of worker node](https://docs.microsoft.com/en-us/virtualization/windowscontainers/deploy-containers/version-compatibility?tabs=windows-server-1903%2Cwindows-10-1909). For instance, worker node of OS version 1903 can only run images with OS version 1903 or earlier. In practice, we suggest to **use same OS version** for image and worker node to avoid potential issues. 

Let's go through an example to demonstrate this process:

1. Create a Kubernetes cluster containing Windows node on Azure following [this tutorial](https://docs.microsoft.com/en-us/azure/aks/windows-container-cli) (At the time writing this doc, Kubernetes version 1.14.6 used in the tutorial is no longer available in the region. You may need to use a later version such as 1.14.8)
2. Deploy OneDev server into created cluster following [this guide](deploy-into-k8s.md)
3. Visit job executors page in administration menu of OneDev, delete the default auto-discover executor, and add a Kubernetes executor with below label selectors (assume name of Windows node pool is _npwin_):

  |Label Name|Label Value|
  |---|---|
  |agentpool|npwin|
4. Get build number of one of the Windows node with below command:

  ```
  kubectl get node <node name> -o jsonpath={.status.nodeInfo.kernelVersion} | awk -F'.' '{print $3}'
  ```
  Node name can be listed by running command `kubectl get nodes`
5. Map build number to OS version with below table:

  |Build Number | OS Version |
  |---|---|
  |18363|1909|
  |18362|1903|
  |17763|1809|
  |17134|1803|
  |16299|1709|
  |14393|1607|   
6. Create a project in OneDev, and add file with name _.onedev-buildspec_ from web UI directly
7. Add a demonstration CI job, with below settings:

  |Image|Command|
  |---|---|
  |`mcr.microsoft.com/windows/servercore:<OS version from above step>`|echo hello world|
  
8. Save and run the job. The job may take much longer than Linux based jobs for the first run, due to the fact that Windows image is much larger

**NOTE**: For fields accepting variables in build spec, make sure to use double slash as Windows path separator as single back slash is treated as escape character