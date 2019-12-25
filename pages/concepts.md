# Concepts
------

### Role

Role defines a set of permissions. When a project is authorized to a user or group, the role must be specified to determine the actual permissions 

### Pull Request

Pull request plays a key role to do code review and work submission in OneDev. It works a bit different from other products: you do not have a merge button to merge the pull request explicitly. Instead, OneDev will merge the pull request into target branch automatically as long as all branch protection requirements are satisfied. 

  User submitting the pull request will be considered as an approver if he/she matches reviewer criteria specified in branch protection setting. For pull requests submitted by users without write permission, OneDev enforces an implicit rule to require someone with write permission to review.

  This approach has below advantages:
  
  1. The user responsible for merge acts as a reviewer to go through the ordinary review process, and can be picked by OneDev automatically based on review rule and change history. 
  1. The same branch protection rule will be applied to both code push and pull request to ensure consistent quality gates.
  1. Instead of merge locally, one can tell OneDev to merge automatically after build is successful.

### Build Spec

Build spec describes specification of build processes in OneDev. It is defined in file _onedev-buildspec_ in root of the repository

### Job

Job describes a unit of build execution, and is defined in build spec. Jobs can depend on each other to accomplish complex build workflows. Each run of a job will generate a build

### Job Workspace

Workspace is the working directory where job executes its commands. Repository and dependency files (if there is any) will be retrieved into this directory. Artifact/report publishing will also be based on this directory

### Build

Build is result of a job run

### Build Stream

Two builds are on same stream if below conditions are met:
* Belongs to same project
* Belongs to same job
* Corresponding commits are on the same branch