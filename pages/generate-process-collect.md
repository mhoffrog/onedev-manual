### Usage Scenario

Generate files in one job, process each file concurrently in the second job, and collect processed results in the third job

### How to Set Up

1. Define a groovy script to get list of published artifact names from upstream build whose number is passed via parameter _Upstream-Build-Number_:

  ![Get File Names From Upstream](../images/generate-process-collect/get-file-names-from-upstream.png)
  
  Content of the script:
  ```groovy
  import io.onedev.server.OneDev
  import io.onedev.server.entitymanager.BuildManager

  // Variable "build" represents the build being triggered currently
  // For single value parameter, just use the first one
  def upstreamBuildNumber = build.paramMap["upstream-build-number"][0]
  def upstreamBuild = OneDev.getInstance(BuildManager.class).find(build.project, upstreamBuildNumber as Long)
  return upstreamBuild.artifactsDir.listFiles().collect {it.name}
  ```
  
1. Edit build spec to add job _Generate Files_ with below command:

  ![Generate Files Job](../images/generate-process-collect/generate-files-job.png)
  
  Command to generate files:
  ``` bash
  echo 1 > file1
  echo 2 > file2
  echo 3 > file3
  ```
1. Add  job _Process File_ with parameter _file_ holding name of the file to be processed

  ![Process File Job](../images/generate-process-collect/process-file-job.png)
  
  For demonstration purpose, the command simply prepend message _processed_ to the file content:
  ``` bash
  echo "processed $(cat @params:file@)" > @params:file@
  ```