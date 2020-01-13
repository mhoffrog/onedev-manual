# Develop Built-in Plugins
------------

Built-in plugins ships together with OneDev, and requires OneDev source code to develop. Follow below steps to add a new built-in plugin project:

1. First follow [this guide](development-environment-setup.md) to set up OneDev development environment

2. Add a new plugin project by adding a new Maven module:  
  
   ![add-new-module](../images/develop-built-in-plugins/add-new-module.png)      
   
3. In next page, specify module name. The module name should follow the convention of _server-plugin-<plugin name>_. And the parent project should be specified as _server-plugin_. Also make sure **NOT** to check the _create a simple project_ option

    ![specify-module-name](../images/develop-built-in-plugins/specify-module-name.png)
   
4. Click the next button to go to next page. If this is the first time you adding a OneDev plugin, you will need to click the _configure_ button to add OneDev remote archetype catalog. The catalog url is: 
   https://artifact.pmease.com/artifactory/pmeaseRepo/archetype-catalog.xml. Apply and close the catalog adding dialog, Eclipse should list all archetypes relating to OneDev. If you added the catalog before, just input _io.onedev_ to filter the archetype

   ![add-archetype-catalog](../images/develop-built-in-plugins/add-archetype-catalog.png)

5. From OneDev archetype list page, choose the archetype **matching** your current OneDev version (Check OneDev server pom file to find current version)

   ![select-onedev-archetype](../images/develop-built-in-plugins/select-onedev-archetype.png)   

6. In the next page, specify group id and version. For built-in plugin project, group id must always be _io.onedev_, and version will actually be ignored (always use current OneDev version) 

   ![specify-group-id-and-artifact-id](../images/develop-built-in-plugins/specify-group-id-and-artifact-id.png)    

7. Finish adding the plugin. Eclipse will take a while to build the newly added plugin. Then edit file _pom.xml_ of project _server-product_ to make it depends on the newly added plugin

   ![add-dependency-to-product](../images/develop-built-in-plugins/add-dependency-to-product.png)