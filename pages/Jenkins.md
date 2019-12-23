Assume we have a project named _test_ at OneDev side. The clone url is http://matrix:6610/projects/test.

  ![project.png](images/project.png)


### Set up Jenkins to report build status

1. At OneDev side, add an user to be used by Jenkins to access the _test_ project. This user should have _Code Write_ permission over the project.
   
    ![onedev-build-account.png](images/onedev-build-account.png)
  
1. At OneDev side, add a build configuration to hold build information reported by Jenkins.
	
    ![onedev-build-configuration.png](images/onedev-build-configuration.png)
	
1. At OneDev side, generate access token for user _build_ as below. This token will be used at Jenkins side in the next step.

    ![generate-user-token.png](images/generate-user-token.png)
    
1. At Jenkins side, make sure you have below plugins installed:
    * Git plugin
    * GitHub plugin
    * GitHub Pull Request Builder plugin

    Remember to restart Jenkins after installing plugins.

1. At Jenkins side, navigate to credential page to add global credentials like below:

    ![add-jenkins-credential.png](images/add-jenkins-credential.png)
    
    We need to add two global credentials here. One is of type _username with password_ and the content is as below:
   
    ![jenkins-username-password-credential.png](images/jenkins-username-password-credential.png)
    
    And the other is of type _secret text_ and the content is as below:
    
    ![jenkins-secret-text-credential.png](images/jenkins-secret-text-credential.png)
        
1. From Jenkins home page, follow the link _Manage Jenkins_, _Configure System_, and then add a GitHub server in _GitHub_ section as below:

    ![jenkins-add-github-server.png](images/jenkins-add-github-server.png)

    OneDev mimics GitHub RESTful API, so that Jenkins can connect to OneDev via existing GitHub plugin. Click _Test Connection_ button to check connection to OneDev. Below message will be displayed if connection is OK:
    ```
    Credentials verified for user build, rate limit: 1000000
    ````
    
1.  At Jenkins side, create a freestyle project _test_, with below settings:
    
    * Specify source code management as Git like below:
     
         ![jenkins-scm.png](images/jenkins-scm.png)
     
    * Add a post-build action of type _Set GitHub Commit Status (universal)_ with below content:

        ![jenkins-post-build-action.png](images/jenkins-post-build-action.png)
     
    * Add appropriate build steps to build the project. 
    
1. At Jenkins side, run the _test_ job. After build finishes, check commits page at OneDev side and we will see that corresponding commits are marked with build status.

    ![jenkins-commit-status.png](images/jenkins-commit-status.png)
        
### Set up Jenkins to verify pull requests

1. Make sure Jenkins has been [set up to report build status](#set-up-jenkins-to-report-build-status) to OneDev.

1. From Jenkins home page, follow the link _Manage Jenkins_, _Configure System_, and then add a GitHub server in _GitHub Pull Request Builder/GitHub Auth_ section as below:

    ![jenkins-github-pullrequest-server.png](images/jenkins-github-pullrequest-server.png)
    
    Then click the _Test Credentials_ button to test the connection as below:
    
    ![jenkins-pullrequest-githubserver-test.png](images/jenkins-pullrequest-githubserver-test.png)
    
1. At Jenkins side, edit _general_ section of the _test_ project to specify GitHub project url, which is the same as clone url:

    ![jenkins-github-project-url.png](images/jenkins-github-project-url.png)
    
1. At Jenkins side, edit _Soucrce Code Management_ section of the _test_ project to specify Refspec as `+refs/pull/*:refs/remotes/origin/pr/*` (in advanced setting of the repositories definition), and branch specifier as `${sha1}`

    ![jenkins-pullrequest-repository.png](images/jenkins-pullrequest-repository.png)

1. At Jenkins side, edit _Build Triggers_ section of the _test_ project:

    * select GitHub API server for pull request we configured previously:
 
        ![jenkins-build-trigger.png](images/jenkins-build-trigger.png)
        
    * In _Advanced_ setting of the section, tick the option _Build every pull request automatically without asking_

        ![jenkins-build-trigger-advanced.png](images/jenkins-build-trigger-advanced.png)
        
    * In _Trigger Setup_ setting of the section, specify commit status context as _ci_ (it will appear as verification name at OneDev side)

        ![jenkins-build-trigger-trigger-setup.png](images/jenkins-build-trigger-trigger-setup.png)

1. At Jenkins side, delete the post build action _Set GitHub commit status (universal)_, as the build trigger we set up in previous step can post commit status to OneDev
   
1. At OneDev side, add a branch protection rule to require Jenkins build.

    ![jenkins-branch-protection.png](images/jenkins-branch-protection.png)
    
    For brevity, we do not specify any mandatory reviewers here. The pull request will be merged automatically (unless the merge strategy is specified as "Do Not Merge") after build succeeds. 
        
1. Now let's create a pull request to test the setup.

    ![pullrequest-waiting-build.png](images/pullrequest-waiting-build.png)

    We will see that the pull request is waiting for Jenkins to build it. After Jenkins builds successfully, the pull request will be merged automatically. 
    
    ![pullrequest-merged-after-build.png](images/pullrequest-merged-after-build.png)
