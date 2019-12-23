OneDev allows to select a range of text while comparing revisions to create permanent links or add comments. However some selections are considered invalid:

1. If the selection contains unexpanded lines like below:

    ![invalid-selection1.png](../images/invalid-selection1.png)
  
    In this case, you need to expand contained lines and select them again.
  
1. If begin and end of the selection are on different revision like below:

   ![invalid-selection2.png](../images/invalid-selection2.png)
  
   ![invalid-selection3.png](../images/invalid-selection3.png)

As long as selection begin and end are on same revision, the selection will be valid even if the selection body contains other revision as below:
  
   ![valid-selection1.png](../images/valid-selection1.png)
  
   ![valid-selection2.png](../images/valid-selection2.png)