# Upgrade Guide
-------

Based on your chosen method, the upgrade procedure diffs:

* If you are [running OneDev as docker container](run-as-docker-container.md), the upgrade happens automatically every time you start the container
* If you are [deploying OneDev into Kubernetes](deploy-into-k8s.md):
  1. Edit file _/path/to/k8s-resources/production/kustomization.yaml_ to change property _newTag_ to a new [OneDev version](https://code.onedev.io/projects/onedev-server/builds?query=%22Job%22+is+%22Release%22) (for instance _3.0.4_). **Never** change the property to an elder version
  2. Run command `kubectl apply -k .` from the production directory
* If you are [running OneDev on bare metal machine](run-on-bare-metal-machine.md):
  1. Assume OneDev is installed at _/opt/onedev_, stop OneDev by running command _/opt/onedev/bin/server.(sh|bat) stop_
  1. Make sure database server is up and running if you are using external database
  1. Extract new OneDev version to a separate folder, say _/path/to/new-onedev
  1. Open a command window and change to directory _/path/to/new-onedev/bin_
  1. Run command _./upgrade.(sh|bat) /opt/onedev_ to perform the upgrade
  1. _/opt/onedev_ will be upgraded and you may launch it to check if things are in order
  1. You may remove _/path/to/new-onedev_ afterwards if everything is fine