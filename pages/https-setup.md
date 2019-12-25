# Https Setup
----------

* If you obtain certificate from a well-known issuer, and have a [reverse proxy setup](reverse-proxy-setup.md), just install the certificate into the front-end web server following its user guide. Nothing needs to be done at OneDev side
   
* If you obtain SSL certificate from well-known issuer, and do not have a [reverse proxy setup](reverse-proxy-setup.md), please follow [this guide](install-key-and-cert.md)

* If you have a [reverse proxy setup](reverse-proxy-setup.md) which uses a self-signed certificate, you will need to configure OneDev to [trust the self-signed certificate](trust-self-signed-certificate.md)

* If you want to use self-signed certificate, and do not have a [reverse proxy setup](reverse-proxy-setup.md):
  1. Run the following OpenSSL command to generate your private key and public certificate. Answer the questions and enter dns name of OneDev server when prompted
  ```bash
  openssl req -newkey rsa:2048 -nodes -keyout your-private-key.pem -x509 -days 365 -out your-cert.pem
  ```
  1. Install generated private key and certificate into OneDev [following this guide](install-key-and-cert.md)