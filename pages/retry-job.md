### Usage Scenario

Retry jobs upon Kubernetes worker node error

### How to Set Up

In section _Retry Upon Failure_ of the job, configure _Retry Condition_ to detect appropriate worker node error. For instance on Google Kubernetes Engine, if a node goes down the log will normally contains such line:

```
Error from server: Get https://<ip address>:<port>/containerLogs/k8s-test-53/job/main?follow=true&timestamps=true: EOF
```

Or this line:

```
Error from server: Get https://<ip address>:<port>/containerLogs/k8s-test-49/job/main?follow=true&timestamps=true: ssh: rejected: connect failed (Connection refused)
```

So we can write the retry condition as below:

```
"Log" contains "Error from server" and ("Log" contains "EOF" or "Log" contains "Connection refused")
```