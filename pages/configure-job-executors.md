# Configure Job Executors
----

Job executor determines where to execute a build job, and can be defined in administration menu. OneDev currently supports two executor types:

1. Docker executor

    Run build job inside docker container of local host

2. Kubernetes executor 

    Run job as pod in Kubernetes cluster
    
There is also a default auto-discover executor dispatching build jobs to either Docker or Kubernetes executor based on current environment:

* If you are [running OneDev as a docker container](run-as-docker-container.md)
  
  The auto-discover executor configures a docker executor to run build jobs as docker containers on local host
 
* If you are [deploying OneDev into a Kubernetes cluster](deploy-into-k8s.md)

  The auto-discover executor configures a Kubernetes job executor to run build jobs as pods on current Kubernetes cluster
  
* If you are [running OneDev on a bare metal machine](run-on-bare-metal-machine.md)

  The auto-discover executor first checks if it can connect to a Kubernetes cluster by running _kubectl cluster-info_. If yes, a Kubernetes executor will be configured; otherwise a docker executor will be used. Note that to use docker executor in this case, you need to add the user running OneDev process to docker group