# Use Self-signed Certificate
-------
1. Run the following OpenSSL command to generate your private key and public certificate. Answer the questions and enter dns name of OneDev server when prompted
  ```bash
  openssl req -newkey rsa:2048 -nodes -keyout private.pem -x509 -days 365 -out public.pem
  ```
1. Combine your key and certificate in a PKCS#12 keystore file
  ```bash
  openssl pkcs12 -inkey private.pem -in public.pem -export -out onedev.pfx
  ```
1. Install the generated keystore into OneDev [following this guide](install-keystore.md)