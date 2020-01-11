A Five Minutes Tutorial
---

This tutorial helps you trying out OneDev on your local development machine

### Procedure

1. Run below command on Linux or Mac OS X to start OneDev in docker mode ([other installation methods](installation-guide.md) also available if you want to explore more):

  ```
  docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker -v $(pwd)/onedev:/opt/onedev -p 6610:6610 1dev/server
  ```

1. Access url `http://<onedev host>:6610` to set up OneDev

1. From OneDev projects page, add a project, say _my-app_. For demonstration purpose, run below command from your terminal to create a react application:

  ```
  npx create-react-app my-app
  ```
  
1. Change into directory _my-app_, and run below command to push code to OneDev:

  ```
  git remote add origin http://<OneDev host>:6610/projects/my-app
  git push origin master:master
  ```
  Input administration account you've specified above as git credential
  
1. Visit files page of project _my-app_ from OneDev, click link _add build spec_ to bring up the GUI to add build specification. For typical projects, OneDev suggests default job templates like below:

  ![Add Job Wizard](../images/add-job-wizard.png)
  
1. Just use the default template, and save the spec. Now you will see that a CI build is running:

  ![After Add Ci Job](../images/after-add-ci-job.png)
    
### Further Reading  

* [Deploy OneDev into your Kubernetes cluster](deploy-into-k8s.md) and get a build farm
* Get to know how to configure OneDev for [typical usage scenarios](usage-scenarios.md)