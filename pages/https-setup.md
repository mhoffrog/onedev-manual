# Https Setup
----------

To enable https support,  either get a SSL certificate from a well-known certificate distributor, or generate a self-signed certificate. 

### Use certificate from well-known certificate distributor

If you've [set up reverse proxy](reverse proxy setup), install the certificate into Apache or Nginx following its usage guide. Otherwise follow below guide to install the certificate into OneDev:

1. Run below command to generate pkcs keystore file from your certificate and private key:

  ```bash
  openssl pkcs12 -export -out onedev.pfx -inkey /path/to/your-private-key -in /path/to/your-cert
  ```
1. If you are [running OneDev as docker container](run-as-docker-container.md), restart the container with below command to enable https support:
    ```bash
    docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker -v /opt/onedev:/opt/onedev -v ${onedev-keystore}:/opt/onedev/conf/onedev.pfx -e https_port=6643 -e keystore=/opt/onedev/conf/onedev.pfx -e keystore_password=${onedev-keystore-password} -p 6643:6643 1dev/server
    ```
    Here ${onedev-keystore} should be replaced with path to onedev.pfx generated above, and ${onedev-keystore-password} should be replaced with specified password when generate the keystore
 
1. If you are [deploying OneDev into Kubernetes](deploy-into-k8s.md):
    * Change to directory _/path/to/k8s-resources/ssl_