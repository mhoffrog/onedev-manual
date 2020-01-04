A Five Minute Tutorial
---

This tutorial demonstrates how to set up a project with git repository, issue tracking and continuous integration.

1. Run below command to start OneDev in docker mode ([other installation methods](installation-guide.md) also available if you want to explore more):

  ```
  docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker -v /opt/onedev:/opt/onedev -p 6610:6610 1dev/server
  ```
  
1. Access url `http://<onedev host>:6610` to set up OneDev

1. From the projects page, add a project, say _my-app_. For demonstration purpose, we will use react-create-app to create an application:

  ```
  npx create-react-app my-app
  ```
  
1. Change into directory _my-app_, and run below command to push code to OneDev:

  ```
  git remote add origin http://<OneDev host>:6610/projects/my-app
  git push origin master:master
  ```
  Input administration account you've specified when set up OneDev as git credential
  
1.