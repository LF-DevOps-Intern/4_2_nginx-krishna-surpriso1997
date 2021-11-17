### Assignment no 5: Reverse proxy all http traffic of port 82 to port 85.

[Continuing from assingment number 4](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/tree/master/4)

Now the following steps are done to proxy pass port 85 to port 82:

1. Create a reverse-proxy.conf file with following values and creating a symlink to /etc/nginx/sites-enabled:

   ```
    server{
       listen 85;

       location /{

               proxy_pass http://localhost:82;

               }
   }

   ```

   ![reverse-proxy.conf file content](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/5/screenshot/reserse-proxy-conf.png)

   ![reverse-proxy.conf at sites-enabled](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/5/screenshot/reverse-conf.png)

There is already a test2.conf for hadling the request on portt 82

2. Restart nginx with ` sudo systemctl restart nginx`

3. Test `localhost:85` on the browser

   ![Testing in the browser](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/5/screenshot/running-on-port-85.png)
