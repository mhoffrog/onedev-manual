# Usage Scenarios
------

### Repository
* [Fork and clone project](fork-clone.md)
* [Get notification when files under folder _src/core_ are changed on master branch](commit-notification.md)

### Issue
* [Add custom field _Platform_ and _Kernel Version_. _Kernel Version_ should be displayed only when _Platform_ is specified as _Linux_](issue-conditional-field.md)
* [Fix issues via commit message to link issues, commits, builds and pull requests](fix-issues-via-commit-message.md)
* [Add custom field _Module_ and assign issue of particular module to module leader automatically](default-assignee.md)

### Pull Request
* [Run CI job against merged commit of pull request only if the pull request changed files under _src_ folder](pull-request-build.md)
* [Require at least two members from expert group to approve if a pull request changed files under _src/core_ folder](pull-request-reviewer.md)

### Build
* [Specify build version when manually trigger a build](specify-build-version.md)
* [Test against any combination of _Oracle/MySQL_ and _Linux/Windows_ upon master branch committing](matrix-build.md)
* [Create an issue and assign to committer automatically when build fails; Close the issue automatically when subsequent build succeeds again](assign-build-failure-investigator.md)

### Permission
* [Anonymous user can only access release builds of certain projects](anonymous-access.md)
* [Release builds can only be generated from master branch](release-on-master.md)
* [Only release builds from master branch of certain projects can be deployed into production cluster, all other builds should use the test cluster](production-cluster.md)