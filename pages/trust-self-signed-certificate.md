# Trust Self-Signed Certificate
---

In case a self-signed certificate is used in [reverse proxy setup](reverse-proxy-setup.md), OneDev should be configured to trust the certificate, otherwise, builds running in Kubernetes cluster will have issues talking to OneDev server

1. If you are [running OneDev as docker container](run-as-docker-container.md):
    * Copy the public certificate in PEM format into a **folder** on host machine, say _/path/to/trust-certs_
    * Restart OneDev container with below command:
      ```bash
      docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker -v /opt/onedev:/opt/onedev -v /path/to/trust-certs:/opt/onedev/conf/trust-certs -e trust_certs=trust-certs -p 6610:6610 1dev/server
      ```
1. If you are [deploying OneDev into Kubernetes](deploy-into-k8s.md):
    *  Edit _/path/to/k8s-resources/trust-certs/kustomization.yaml_ to add absolute path to public certificate in PEM format under _files_ section
    * Run command `kubectl apply -k .` from directory _/path/to/k8s-resources/trust-certs_ to apply the change

1. If you are  [running OneDev on bare metal machine](run-on-bare-metal-machine.md):
    * Copy the public certificate in PEM format into folder _/opt/ondev/conf/trust-certs_ (assume OneDev is installed at _/opt/onedev_, same as below)
    * Edit file _/opt/onedev/conf/server.properties_ to uncomment property _trust_certs_:
      ```properties
      trust_certs=trust-certs
      ```
    * Restart OneDev server to take the change into effect