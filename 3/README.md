### Assignment 3: Nginx Reverse proxy all http requests to nodes js api.

The following steps are followed :

1.  The node api created in previous assignment is started with pm2 as :

    ```
    npx pm2 start process.config.js

    ```

2.  A new configuration file node.confg is created at ``/etc/nginx/sites-available`and linked to`/etc/nginx/sites-enabled/```.
    The configuration file contains the following details:

    ```
    server {
    listen 80;

        root /var/www/html;

        index index.html index.htm index.nginx-debian.html;

        server_name localhost;

        location / {

                proxy_pass http://localhost:6080;

                try_files $uri $uri/ =404;
        }
    ```

    }

        ```

    ![node.conf file](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/3/screenshot/nod.conf-nginx-file.png)

3.  Restart nginx service
    nginx service is restarted with :

    ```
        sudo systemctl restart nginx
    ```

4.  Testing the node app running on port 6080

    ![Node app running on pot 6080](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/3/screenshot/node-app-running-on-port-6080.png)

5.  Testing the node app running on port 80

    ![Node app running on port 80 after proxy pass](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/3/screenshot/node-app-running-on-port-80.png)
