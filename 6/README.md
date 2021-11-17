### Assignment number 6: Install LEMP stack (avoid installing mysql) and open info.php on port 80 and print message info.php.

The following steps are carried out:

1.  Installing php's dependencies :

    ```
    sudo apt install php php-fpm
    ```

    ![Installing php](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/6/screenshot/php-install.png)

    ![Php fpm service runnign status](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/6/screenshot/php-service.png)

2.  Created a directory /var/www/php and created an info.php file with following php script:

    ```
    <?php
         phpinfo();
     ?>
    ```

    ![info.php](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/6/screenshot/info.php.png)

    where phpinfo() function dissplays an infomation abut th installed php distributon.

3.  created a php.conf file at /etc/nginx/sites-available and create a symlink to /etc/nginx/sites0enabled:

    ```
    server {

        listen 80;

        root /var/www/html;

        index index.php index.html index.htm index.nginx-debian.html;

        server_name your_domain;

        location / {

                try_files $uri $uri/ =404;

        }
        location ~ \.php$ {

                include snippets/fastcgi-php.conf;

                fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;

        }

        location ~ /\.ht {

                deny all;

        }
    ```

        here the php app is proxy passed by fast cgi server to the php app server.

        ![php.conf](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/6/screenshot/php.conf.png)

    }

4.  tesing in the browser

    ![Running info.php on port 80](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/6/screenshot/php-site-inbrowser.png)
