# Https Setup
----------

* Use certificate from well-known issuer, and have a [reverse proxy setup](reverse-proxy-setup.md). In this case, just install the certificate into Apache or Nginx following its user guide.
   
* Follow [this guide](use-certificate-from-well-known-issuer-without-reverse-proxy.md) if you obtain SSL certificate from well-know issuer, and do not have a [reverse proxy setup](reverse-proxy-setup.md)

* Follow [this guide](use-self-signed-certificate-with-reverse-proxy.md) if you have a [reverse proxy setup](reverse-proxy-setup.md) which uses a self-signed certificate

* Follow [this guide](use-self-signed-certificate-without-reverse-proxy.md) if you want to use self-signed certificate, and do not have a [reverse proxy setup](reverse-proxy-setup.md)