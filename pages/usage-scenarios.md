# Usage Scenarios
------

### Repository
* [Fork and clone project](fork-clone.md)

### Issue
* [Fix issues via commit message to link issues, commits, builds and pull requests](fix-issues-via-commit-message.md)

### Pull Request
* [Run CI job against merged commit of pull request only if the pull request changed files under _src_ folder](pull-request-build.md)
* [Require at least two members from expert group to approve if a pull request changed files under _core_ folder](pull-request-reviewer.md)

### Build Set Up
* [Specify build version when manually trigger a build](specify-build-version.md)
* [Test against any combination of _Oracle/MySQL_ and _Linux/Windows_ upon master branch commit](matrix-build.md)

### Permission Control
* [Anonymous user can only access release builds of certain projects](anonymous-access.md)
* [Release builds can only be generated from master branch](release-on-master.md)
* [Only release builds from master branch of certain projects can be deployed into production cluster, all other builds should use the test cluster](production-cluster.md)