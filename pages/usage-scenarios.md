# Usage Scenarios
------

### Repository
* [Fork and clone project](fork-clone.md)
* [Get notification when files under folder _src/core_ are changed on master branch](commit-notification.md)

### Pull Request
* [Run CI job against merged commit when pull request changed files under _src_ folder](pull-request-build.md)
* [Require at least two members from expert group to approve if a pull request changed files under _src/core_ folder](pull-request-reviewer.md)

### Issue
* [Fix issues via commit message to link issues, commits, builds and pull requests](fix-issues-via-commit-message.md)
* [Add custom field _Platform_ and _Kernel Version_. _Kernel Version_ should be displayed only when _Platform_ is specified as _Linux_](issue-conditional-field.md)
* [Continue with above scenario. For all open Windows issues assigned to tommy or jerry, reassign to robin](batch-assign.md)
* [Create an issue board to show open issue assignment between different users](assignment-board.md)
* [Add custom field _Module_ and assign issue of particular module to module leader automatically](default-assignee.md)
* [Auto-transit issue to custom state _Deployed_ when build fixing it is deployed](issue-deployed.md)
* [Auto-transit issue to custom state _In Review_ when relevant pull request is opened](issue-in-review.md)
* [Add custom state _Verified_. Only Tester role can transit issues to this state. Further, the transition is applicable for all issue types except Task](issue-verified.md)

### Build
* [Specify build version when manually trigger a build and create a corresponding tag if build is successful](specify-build-version.md)
* [Prompt for _Platform_ and _Kernel Version_ when manually trigger a build. _Kernel Version_ should be displayed only when _Platform_ is specified as _Linux_](build-conditional-param.md)
* [Test against any combination of _Oracle/MySQL_ and _Linux/Windows_ upon master branch committing](matrix-build.md)
* [Auto-create an issue and assign to committer for investigation upon build failure on master branch; Auto-close the issue when subsequent build succeeds again](assign-build-failure-investigator.md)
* [Generate files in one job, process each file concurrently in the second job, and collect processed result in the third job](generate-process-collect.md)
* [Retry jobs upon Kubernetes worker node error](retry-job.md)
* [Use MySQL service while running the job](mysql-service.md)
* [Run build on windows node in Kubernetes cluster](k8s-windows-node.md)

### Security

* [Use secret value in build spec](build-spec-secret.md)
* [Anonymous user can only access release builds of certain projects](anonymous-access.md)
* [Release builds can only be generated from master branch](release-on-master.md)
* [Only release builds from master branch of certain projects can be deployed into production cluster, all other builds should use the test cluster](production-cluster.md)