Scripting can be used in OneDev in a number of places to achieve flexibility. The script needs to be written in [groovy](http://groovy-lang.org/) and the variable _onedev_ is passed to the script. 

### Scripting when define issue custom field  
When define issue custom field, scripting can be used to define show condition, field choices, and default field value. Assume we have below requirement:

1. When create the issue, user should be able to select which module the issue belongs to, and the module should be selected from available groups (the system is set up to define corresponding group for each module)
2. When create the issue and select the module, the system should assign the issue to the module leader by default, and reporter can assign the issue to other member in the module if necessary

To achieve this:

1. Define a custom field named _Module_ with type set to _Choice_, and the _Available Choices_ option defined to execute below script:

```groovy
import io.onedev.server.manager.GroupManager;

def choices = [:];
for (group in onedev.getInstance(GroupManager.class).query()) {
    choices.put(group.name, null);
}

return choices;
````
2. Define a custom field named _Assignee_ with type set to _User choice_, and the _Available Choices_ option defined to execute below script:

```groovy
import io.onedev.server.manager.GroupManager;

def module = onedev.editContext.getInputValue("Module");

def choices = [];
if (module != null) {
    for (user in onedev.getInstance(GroupManager.class).find(module).members) {
        choices.add(user.facade);
    }
}	
return choices;
```    
    
3. Define _Default Value_ of the _Assignee_ field to execute below script:

```groovy
import io.onedev.server.manager.GroupManager;

def module = onedev.editContext.getInputValue("Module");

if (module == "Front End")
    return "tracy";
else if (module == "Back End")
    return "robin";
else
    return null;
```
