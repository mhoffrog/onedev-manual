Pull request plays a key role to do code review and work submission in OneDev. It works a bit different from other products: you do not have a merge button to merge the pull request explicitly. Instead, OneDev will merge the pull request into target branch automatically as long as all branch protection requirements are satisfied. 

User submitting the pull request will be considered as an approver if he/she matches reviewer criteria specified in branch protection setting. For pull requests submitted by users without write permission, OneDev enforces an implicit rule to require someone with write permission to review.

This approach has below advantages:
* The user responsible for merge acts as a reviewer to go through the ordinary review process, and can be picked by OneDev automatically based on review rule and change history. 
* The same branch protection rule will be applied to both code push and pull request to ensure consistent quality gates.
* Instead of merge locally, one can tell OneDev to merge automatically after build is successful.