### Assignment 1 : install nginx and host a simple index.html with message “hello nginx”

These are the steps:

1.  Install nginx:
    nginx is installed with the command:

        ```
        sudo apt install nginx

        ```

    ![installed nginx](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/1/screenshot/install-nginx.png)

    nginx's running status can be checked with :

        ```
        sudo systemctl status nginx
        ```

    ![Nginx running status](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/1/screenshot/nginx-running-status.png)

2.  Create or update `index.html` file at ` /var/www/html` and set the message `hello nginx`

        ![Added hello nginx message in inde.html ](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/1/screenshot/index-html.png)

3.  Create assignment-1.confg in /etc/nginx/sites-availele and link it to /etc/ngin/sites-enabled with the following configuration

        ```
        server {

                listen 80;

                listen [::]:80;

                root /var/www/localhost/html;

                index index.html index.htm index.nginx-debian.html;

                server_name localhost;

                location / {

                        try_files $uri $uri/ =404;

                }

            }

        ```

    Restart nginx with the command:

        ```
            sudo systemctl restart nginx
        ```

4.  visit localhost in browser

    ![nginx running on default port in browser](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/1/screenshot/hello-nginx-assignment-1.png)
