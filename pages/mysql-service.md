### Usage Scenario 

Use MySQL service while running job

### How to Set Up

1. In section _Dependencies & Services_ to add a service like below:

  ![Mysql Service](../images/mysql-service.png)
  
  Note that for MySQL root password, we are referencing secret _db-password_ defined in [this tutorial ](build-spec-secret.md)
  
1. If the job runs with a Kubernetes executor and if you want to run MySQL  service on particular nodes, configure service locator in section _More Settings_ of the executor like below:

  ![Service Locator](../images/service-locator.png)