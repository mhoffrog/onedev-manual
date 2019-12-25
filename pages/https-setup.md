# Https Setup
----------

* If you obtain certificate from a well-known issuer, and have a [reverse proxy setup](reverse-proxy-setup.md), just install the certificate into Apache or Nginx following its user guide. Nothing needs to be done at OneDev side
   
* If you obtain SSL certificate from well-known issuer, and do not have a [reverse proxy setup](reverse-proxy-setup.md), please follow [this guide](use-certificate-from-well-known-issuer.md)

* If you have a [reverse proxy setup](reverse-proxy-setup.md) which uses a self-signed certificate, you will need to configure OneDev to [trust the self-signed certificate](trust-self-signed-certificate.md)

* If you want to use self-signed certificate, and do not have a [reverse proxy setup](reverse-proxy-setup.md), please follow [this guide](use-self-signed-certificate.md)