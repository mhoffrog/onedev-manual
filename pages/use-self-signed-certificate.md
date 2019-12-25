# Use Self-signed Certificate
-------
1. Run the following OpenSSL command to generate your private key and public certificate. Answer the questions and enter dns name of OneDev server when prompted
  ```bash
  openssl req -newkey rsa:2048 -nodes -keyout your-private-key.pem -x509 -days 365 -out your-cert.pem
  ```
1. Install generated private key and certificate into OneDev [following this guide](install-key-and-cert.md)