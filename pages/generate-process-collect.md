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
  
1. Edit build spec to