# Development Environment Setup
-----------

1. Make sure you have [JDK 1.8](http://www.oracle.com/technetwork/java/javase/downloads/index.html) installed
1. Make sure you have [Git](https://git-scm.com/) version 2.11.1 or higher installed
1. Install [Eclipse Oxygen or higher](http://www.eclipse.org/) for Java development
1. Install JavaScript development tools and web development tools from Eclipse menu _Help/Install New Software_ like below:

    ![install_js_web_dev.png](../images/development-environment-setup/install_js_web_dev.png)
    
1. Create a new directory as Eclipse workspace, for instance, _/home/robin/workspace_
1. Clone OneDev source code into a sub directory under Eclipse workspace:

    ```
    cd /home/robin/workspace
    git clone https://code.onedev.io/projects/onedev-server
    ```
1. Run Eclipse and open workspace _/home/robin/workspace_
2. Specify JDK instead of JRE as default. Otherwise, Eclipse will not be able to access Java sources to get help

    ![use-jdk-as-default.png](../images/development-environment-setup/use-jdk-as-default.png)
    
2. Edit Maven preferences to check the option _Hide folders of physically nested modules_:

    ![maven-preference.png](../images/development-environment-setup/maven-preference.png)
    
1. Import existing maven projects as below:

    ![import-maven-projects.png](../images/development-environment-setup/import-maven-projects.png)
    -------------
    ![Import Workspace Projects](../images/development-environment-setup/import-workspace-projects.png)
    
1. Wait patiently for Eclipse to download necessary dependencies and build. In case there are compilation errors, update the projects as below:

    ![update-project.png](../images/development-environment-setup/update-project.png)
    
1. After build succeeds, you may run OneDev as below:

    ![run-as-java-application.png](../images/development-environment-setup/run-as-java-application.png)
    ----------
    ![select-bootstrap-class.png](../images/development-environment-setup/select-bootstrap-class.png)
    
    In case OneDev reports _Unable to find product directory_. Please check the _Run Configuration_ and make sure that the project is specified as _server-product_ as below:
    ![Run Configuration Project](../images/development-environment-setup/run-configuration-project.png)