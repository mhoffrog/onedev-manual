A Five Minutes Tutorial
---

This tutorial helps you trying out OneDev on your local machine. Follow [**this tutorial**](test-in-k8s.md) to try build farm in Kubernetes

1. Run below command on Linux or Mac OS X to start OneDev in docker mode:

  ```
  docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker -v $(pwd)/onedev:/opt/onedev -p 6610:6610 1dev/server
  ```
  If you want to try on Windows machine, please follow the [bare metal installation guide](run-on-bare-metal-machine.md)

1. Point your browser to `http://localhost:6610` to set up OneDev. In system setting page, just use suggested server url (`http://localhost:6610`)

1. From OneDev projects page, add a project _my-app_

1. Run below command from your terminal to create a react application:

  ```
  npx create-react-app my-app
  ```
  
1. Change into directory _my-app_, and run below command to push code to OneDev:

  ```
  git remote add origin http://localhost:6610/projects/my-app
  git push origin master:master
  ```
  When prompted, input administrator account specified above as git credential
  
1. Visit files page of project _my-app_ from OneDev, click link _add build spec_ to bring up the GUI to add build specification. For typical projects, OneDev suggests default job templates like below:

  ![Add Job Wizard](../images/add-job-wizard.png)
  
1. Just use the default template, and save the spec. Now you will see that a CI build is running:

  ![After Add Ci Job](../images/after-add-ci-job.png)
    
1. Congrats! You've finished the tutorial. Continue to check [typical usage scenarios](usage-scenarios.md) if you are interested.