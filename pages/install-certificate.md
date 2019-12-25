# Install Certificate into OneDev
---------

1. Run below command to generate pkcs keystore file from your certificate and private key:

  ```bash
  openssl pkcs12 -export -out onedev.pfx -inkey /path/to/your-private-key.pem -in /path/to/your-cert.pem
  ```
1. If you are [running OneDev as docker container](run-as-docker-container.md), restart the container with below command to enable https support:
    ```bash
    docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker -v /opt/onedev:/opt/onedev -v ${onedev-keystore}:/opt/onedev/conf/onedev.pfx -e https_port=6643 -e keystore=/opt/onedev/conf/onedev.pfx -e keystore_password=${onedev-keystore-password} -p 6643:6643 1dev/server
    ```
    Here ${onedev-keystore} should be replaced with **absolute path** to onedev.pfx generated above, and ${onedev-keystore-password} should be replaced with specified password when generate the keystore
 
1. If you are [deploying OneDev into Kubernetes](deploy-into-k8s.md):
    * Run below command to generate base64 encoded keystore into ssl directory of Kubernetes resources:
      ```bash
      base64 ${onedev-keystore} > /path/to/k8s-resources/ssl/onedev.pfx.base64
      ```
      Here ${onedev-keystore} should be replaced with path to onedev.pfx generated above  
    * Edit file _/path/to/k8s-resources/ssl/kustomization.yaml_ to set keystore and password as below:
       ```yaml
       - keystore=onedev.pfx.base64
       - password=<specified password when generate keystore>
       ```
    * Run `kubectl apply -k .` from the _ssl_ directory to redeploy OneDev with https enabled

1. If you are [running OneDev on bare metal machine](run-on-bare-metal-machine.md):
    * Copy file _onedev.pfx_ into directory _/opt/onedev/conf_ (assume OneDev is installed in _/opt/onedev_, same below)
    * Edit file _/opt/onedev/conf/server.properties_ to specify keystore and password as below:
      ```properties
      keystore=onedev.pfx
      keystore_password=<password specified when generate the keystore>
      ```
    * Then restart OneDev to take the change into effect