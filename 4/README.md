### Assignment 4: Create a test2.conf and listen on port 82 and to “ location /test/” with message “ test is successful”.

The following steps are followed:

1. Created a new configuration file test2.conf at `/etc/nginx/sites-available` and symlinked to `/etc/nginx/sites-enabled`:

   The configuration file contained the following properties in the server and location block:

   ```
    server {
       listen 82;
       server_name localhost;
       root /var/www/html;

       location /test/ {
               index index.html test.html test.htm index.htm;
       }
   ```

   Here , the server listens on port 82 and maps /test/ to the root of the server
   }

![test2.conf configuration file](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/4/screenshot/test2.conf.png)

    ```

2. create /var/www/html/test directory and index.html file inside it with the followig content:

   ```
    <!DOCTYPE html>
   <html>
       <body>
           <p> test is successful </p>
       </body>
   </html>

   ```

![index.html file at /var/www/html/test](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/4/screenshot/test-html-at-var-www-html.png)

3. Restart nginx
   nginx service is reatarted with:

   ```
   sysstemctl restart nginx

   ```

4. Test in the browser

    ![testing /test in localhost on port 82 in broser](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/4/screenshot/test-port-82.png)
