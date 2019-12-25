# Reverse Proxy Setup
----------

You may configure OneDev to run behind Nginx or Apache Httpd to do reverse proxying. Below procedure assumes you are running Nginx or Apache Httpd on Ubuntu:

### Nginx

1. Assume your OneDev instance runs at port 6610, and you want to access it via _http://onedev.example.com_. Create a file named _onedev.example.com_ with below content under directory _/etc/nginx/sites-available_:
  ```
server {
        listen 80;
        listen [::]:80;

        server_name onedev.example.com;

        location /wicket/websocket {
                proxy_pass http://localhost:6610/wicket/websocket;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "upgrade";
        }

        location / {
                proxy_pass http://localhost:6610/;
        }
}
```

1. Then, enable this site and restart Nginx server:
  ```
sudo ln -s /etc/nginx/sites-available/git.example.com /etc/nginx/sites-enabled/onedev.example.com
sudo service nginx restart
```

### Apache Httpd

1. Make sure you have Apache httpd server version 2.4.5 or higher installed
1. Enable [mod_proxy](http://httpd.apache.org/docs/2.4/mod/mod_proxy.html) by running:
  ```
  sudo a2enmod proxy_http
  ```
1. Enable [mod_proxy_wstunnel](http://httpd.apache.org/docs/2.4/mod/mod_proxy_wstunnel.html) by running:
  ```
  sudo a2enmod proxy_wstunnel
  ```
1. Now assume your OneDev instance runs at port 6610, and you want to access it via _http://onedev.example.com_. Create a file named _onedev.example.com.conf_ with below content under _/etc/apache2/sites-available_:
  ```
<VirtualHost *:80>
        ServerName onedev.example.com

        ProxyRequests Off

        ProxyPreserveHost Off

        <Proxy *>
                Order deny,allow
                Allow from all
        </Proxy>

        ProxyPass /wicket/websocket ws://localhost:6610/wicket/websocket
        ProxyPass / http://localhost:6610/
        ProxyPassReverse / http://localhost:6610/

        <Location />
                Order allow,deny
                Allow from all
        </Location>

        ErrorLog /var/log/apache2/onedev-error.log
        CustomLog /var/log/apache2/onedev-access.log combined
        LogLevel warn
</VirtualHost>
  ```
1. Then, enable this site and restart Apache httpd server:
  ```
sudo a2ensite onedev.example.com.conf
sudo service apache2 restart
```