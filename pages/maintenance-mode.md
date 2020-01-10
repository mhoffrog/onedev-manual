# Maintenance Mode
----
Some tasks need to be performed in maintenance mode, such as restoring database, resetting administrator password, etc. Below explains how to enter into this mode for different installation flavors:

* If you are [running OneDev as docker container](run-as-docker-container.md):

  1. Stop the container
  1. Run below command to enter into container:

    ```bash
    docker run -it --rm -v $(pwd)/onedev:/opt/onedev 1dev/server bash 
    ```
  1. Change into directory _/opt/onedev_ in the container to perform various maintenance tasks
  
* If you are [deplolying OneDev into Kubernetes cluster](deploy-into-k8s.md):
  1. Change to directory _/path/to/k8s-resources/maintenance_, and run  command `kubectl apply -k .`
  1. Run command `kubectl get pods -n onedev` to check pod name of onedev
  2. Run below command to enter into onedev pod container (replace _<onedev-pod-name>_ with the actual pod name obtained in previous step):
  ```bash
  kubectl exec -it -n onedev <onedev-pod-name> bash
  ```
  3. Change to directory _/opt/onedev_ in the container to perform various maintenance tasks
  4. After performing maintenance tasks, you may start OneDev in normal mode by changing to the production folder and run `kubectl apply -k .`

* If you are [running OneDev on bare metal machine](bare-metal-installation.md):

  1. Stop OneDev service 
  2. Change to the directory where OneDev is installed to perform maintenance tasks